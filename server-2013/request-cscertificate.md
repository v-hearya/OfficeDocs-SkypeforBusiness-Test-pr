---
title: Request-CsCertificate
TOCTitle: Request-CsCertificate
ms:assetid: 24e8ba6f-6023-4c03-a594-5b40784fd16a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425723(v=OCS.15)
ms:contentKeyID: 48183643
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Request-CsCertificate

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Provides a way to request certificates for use with servers running Lync Server and server roles. Also provides a way to check the status of existing certificate requests and, if needed, to cancel any (or all) of those requests. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Request-CsCertificate -New <SwitchParameter> -Type <CertType[]> [-AllSipDomain <SwitchParameter>] [-CA <String>] [-CaAccount <String>] [-CaPassword <String>] [-City <String>] [-ClientEKU <$true | $false>] [-ComputerFqdn <Fqdn>] [-Country <String>] [-DomainName <String>] [-FriendlyName <String>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-KeyAlg <RSA | ECDH_P256 | ECDH_P384 | ECDH_P521>] [-KeySize <Int32>] [-Organization <String>] [-OU <String>] [-Output <String>] [-PrivateKeyExportable <$true | $false>] [-State <String>] [-Template <String>] <COMMON PARAMETERS>

    Request-CsCertificate -List <SwitchParameter> [-RequestId <Int32>] <COMMON PARAMETERS>

    Request-CsCertificate -Retrieve <SwitchParameter> [-RequestId <Int32>] <COMMON PARAMETERS>

    Request-CsCertificate -Clear <SwitchParameter> [-RequestId <Int32>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 creates a new certificate request: it contacts the CA atl-ca-001.litwareinc.com\\myca and requests a new WebServicesExternal certificate.

    Request-CsCertificate -New -Type WebServicesExternal -CA "atl-ca-001.litwareinc.com\myca"

</div>

<div>

## EXAMPLE 2

Example 2 lists all the pending certificate requests made by using the **Request-CsCertificate** cmdlet.

    Request-CsCertificate -List

</div>

<div>

## EXAMPLE 3

Example 3 uses the Output parameter to create an offline certificate request.

    Request-CsCertificate -New -Type WebServicesExternal -Output C:\Certificates\WebServicesExternal.cer

</div>

<div>

## EXAMPLE 4

Example 4 is a more detailed (and more realistic) example of how to use the Request-CsCertificate cmdlet. This example requests a certificate for use with the Standard Edition of Lync Server

    Request-CsCertificate -New -Type Default,WebServicesInternal,WebServicesExternal -ComputerFqdn "atl-cs-001.litwareinc.com" -CA "atl-ca-001.litwareinc.com\myca" -FriendlyName "Standard Edition Certficate" -Template jcila -PrivateKeyExportable $True -DomainName "atl-cs-001.litwareinc.com,atl-ext.litwareinc.com"

</div>

<div>

## EXAMPLE 5

In Example 5, a pool certificate is requested for use with the Enterprise Edition of Lync Server

    Request-CsCertificate -New -Type Default,WebServicesInternal,WebServicesExternal -ComputerFqdn "atl-cs-001.litwareinc.com" -CA "atl-ca-001.litwareinc.com\myca" -FriendlyName "Enterprise Edition Pool Certificate" -Template jcila -PrivateKeyExportable $True -DomainName "pool1.litwareinc.com,pool1int.litwareinc.com,pool1ext.litwareinc.com"

</div>

<div>

## EXAMPLE 6

Example 6 shows how you can request a certificate for the internal Edge Server.

    Request-CsCertificate -New -Type Internal -ComputerFqdn "atl-edge-001" -CA "atl-ca-001.litwareinc.com\myca" -FriendlyName "Internal Edge Certificate" -Template jcila -PrivateKeyExportable $True -DomainName "atl-edge-001.litwareinc.com, ap.litwareinc.com"

</div>

<div>

## EXAMPLE 7

Example 7 is a variation of the command shown in Example 6, In this case, however, the request is for the external Edge Server.

    Request-CsCertificate -New -Type AccessEdgeExternal,DataEdgeExternal,AudioVideoAuthentication -ComputerFqdn "atl-edge-001" -CA "atl-ca-001.litwareinc.com\myca" -FriendlyName "External Edge Certificate" -Template jcila -PrivateKeyExportable $True -DomainName "atl-edge-001.litwareinc.com,ap.litwareinc.com,dp.litwareinc.com,atl-edge-001"

</div>

</div>

<div>

## Detailed Description

Lync Server uses certificates as a way for servers and server roles to verify their identities; for example, an Edge Server uses certificates to verify that the computer it is communicating with really is a Front End Server and vice versa. In order to fully implement Lync Server, you will need to have the appropriate certificates assigned to the appropriate server roles.

One way to request certificates for use with Lync Server is to call the **Request-CsCertificate** cmdlet. Although it is possible to use other standard Windows tools in order to request certificates for use with Lync Server, one major advantage to using the **Request-CsCertificate** cmdlet is the fact that the cmdlet will analyze your topology before contacting the certification authority (CA). Based on that analysis, the **Request-CsCertificate** cmdlet will automatically request a certificate with the proper subject name and subject alternative name fields.

The **Request-CsCertificate** cmdlet is designed to request certificates specifically for use with Lync Server. It is not designed to be an all-purpose certificate management tool.

In addition to requesting new certificates, this cmdlet can also be used to review any pending certificate requests, provided those requests were made using the **Request-CsCertificate** cmdlet. The **Request-CsCertificate** cmdlet can also be used to delete pending certificate requests, as long as those requests were made using the cmdlet.

When attempting to retrieve certificate requests you might receive an error message if you have any revoked requests; currently the **Request-CsCertificate** cmdlet only supports these request types: Issued, Denied, and Pending. If you encounter problems due to a revoked certificate use a command similar to this to clear the revoked request (where 224 is the RequestID of the revoked certificate request):

Request-CsCertificate –Clear –RequestID 224

After that you should be able to retrieve certificate requests.

Who can run this cmdlet: You must be a local administrator and have rights to the specified certification authority in order to run the **Request-CsCertificate** cmdlet locally. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Request-CsCertificate"}

</div>

<div>

## Parameters


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Required</th>
<th>Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Clear</em></p></td>
<td><p>Required</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>When present, deletes any pending certificate requests made by using the <strong>Request-CsCertificate</strong> cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>List</em></p></td>
<td><p>Required</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>When present, lists any pending certificate requests made by using the <strong>Request-CsCertificate</strong> cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><em>New</em></p></td>
<td><p>Required</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>When present, indicates that you want to request a new certificate.</p></td>
</tr>
<tr class="even">
<td><p><em>Retrieve</em></p></td>
<td><p>Required</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>When present, retrieves any pending certificate requests made by using the <strong>Request-CsCertificate</strong> cmdlet and attempts to complete the operation and import the requested certificate.</p></td>
</tr>
<tr class="odd">
<td><p><em>Type</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.CertType[]</p></td>
<td><p>Type of certificate being requested. Certificate types include (but are not limited to):</p>
<p>AccessEdgeExternal</p>
<p>AudioVideoAuthentication</p>
<p>DataEdgeExternal</p>
<p>Default</p>
<p>External</p>
<p>Internal</p>
<p>iPhoneAPNService</p>
<p>iPadAPNService</p>
<p>MPNService</p>
<p>PICWebService (Microsoft Lync Online 2010 only)</p>
<p>ProvisionService (Microsoft Lync Online 2010 only)</p>
<p>WebServicesExternal</p>
<p>WebServicesInternal</p>
<p>WsFedTokenTransfer</p>
<p>For example, this syntax requests a new Default certificate: -Type Default.</p>
<p>You can specify multiple types in a single command by separating the certificate types with commas:</p>
<p>-Type Internal,External,Default</p></td>
</tr>
<tr class="even">
<td><p><em>AllSipDomain</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>When present, all your SIP domains are automatically added to the certificates Subject Alternative Name field. If not present, only the primary SIP domain is added by default. However, additional domains can be specified by using the DomainName parameter.</p></td>
</tr>
<tr class="odd">
<td><p><em>CA</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Fully qualified domain name (FQDN) that points to the CA. For example: -CA &quot;atl-ca-001.litwareinc.com\myca&quot;. To obtain a list of known CAs, type the following at the Windows PowerShell prompt, and then press ENTER:</p>
<p>certutil</p>
<p>The Config property returned by Certutil indicates the location of a CA.</p></td>
</tr>
<tr class="even">
<td><p><em>CaAccount</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Account name of the user requesting the new certificate, using the format domain_name\user_name. For example: -CaAccount &quot;litwareinc\kenmyer&quot;. If not specified, the <strong>Request-CsCertificate</strong> cmdlet will use the credentials of the logged-on user when requesting the new certificate.</p></td>
</tr>
<tr class="odd">
<td><p><em>CaPassword</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Password for the user requesting the new certificate (as specified using the CaAccount parameter).</p></td>
</tr>
<tr class="even">
<td><p><em>City</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>City where the certificate will be deployed.</p></td>
</tr>
<tr class="odd">
<td><p><em>ClientEKU</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Set this parameter to True if the certificate is to be used for client authentication. This type of authentication is required if you want your users to be able to exchange instant messages with people who have accounts with AOL. The EKU portion of the parameter name is short for extended key usage; the extended key usage field lists the valid uses for the certificate.</p></td>
</tr>
<tr class="even">
<td><p><em>ComputerFqdn</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>FQDN of the computer for which the certificate is being requested. When present, this parameter forces the <strong>Request-CsCertificate</strong> cmdlet to connect to the Central Management store in order to locate the specified computer. You should always use the computer name when requesting a certificate, even when requesting a pool certificate. The <strong>Request-CsCertificate</strong> cmdlet will automatically add the pool name to the Subject Name of any certificate obtained using this cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>Country</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Country/region where the certificate will be deployed.</p></td>
</tr>
<tr class="odd">
<td><p><em>DomainName</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Comma-separated list of fully-qualified domain names that should be added to the certificate’s Subject Alternative Name field. For example:</p>
<p>-DomainName &quot;atl-cs-001.litwareinc.com, atl-cs-002.litwareinc.com,atl-cs-003.litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>FriendlyName</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>User-assigned name that makes it easier to identify the certificate.</p></td>
</tr>
<tr class="even">
<td><p><em>GlobalCatalog</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>FQDN of a global catalog server in your domain. This parameter is not required if you are running the <strong>Request-CsCertificate</strong> cmdlet on a computer with an account in your domain.</p></td>
</tr>
<tr class="odd">
<td><p><em>GlobalSettingsDomainController</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>FQDN of a domain controller where global settings are stored. If global settings are stored in the System container in Active Directory Domain Services then this parameter must point to the root domain controller. If global settings are stored in the Configuration container then any domain controller can be used and this parameter can be omitted.</p></td>
</tr>
<tr class="even">
<td><p><em>KeyAlg</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.X509Certificates.KeyAlgorithmIdentifier</p></td>
<td><p>Indicates the type of cryptographic algorithm to be used in generating the public and private keys for the new certificate. Valid key algorithms include:</p>
<p>RSA</p>
<p>ECDH_P256</p>
<p>ECDH_P384</p>
<p>ECDH_P521</p></td>
</tr>
<tr class="odd">
<td><p><em>KeySize</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Int32</p></td>
<td><p>Indicates the size (in bits) of the private key used by the certificate. Larger key sizes are more secure, but require more processing overhead in order to be decrypted.</p>
<p>Valid key sizes are 1024; 2048; and 4096. For example: -KeySize 2048.</p></td>
</tr>
<tr class="even">
<td><p><em>Organization</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Name of the organization requesting the new certificate. For example: -Organization &quot;Litwareinc&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><em>OU</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Active Directory organizational unit for the computer that will be assigned the new certificate.</p></td>
</tr>
<tr class="even">
<td><p><em>Output</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Path to the certificate file. If you want to create an offline certificate request use the Output parameter and specify a file path for the certificate request; for example: -Output C:\Certificates\NewCertificate.pfx. That will create a certificate request file that can then be emailed to a certification authority for processing.</p></td>
</tr>
<tr class="odd">
<td><p><em>PrivateKeyExportable</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Set this parameter to True if you want to make the certificate’s private key exportable. When a private key is exportable, the certificate can be copied and used on multiple computers.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report &quot;C:\Logs\Certificates.html&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>RequestId</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Int32</p></td>
<td><p>Identification number associated with a certificate request. The RequestID parameter provides a way for you to list, retrieve, or clear an individual certificate.</p></td>
</tr>
<tr class="even">
<td><p><em>State</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>U.S. state where the certificate will be deployed. For example: -State WA.</p></td>
</tr>
<tr class="odd">
<td><p><em>Template</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Indicates the certificate template to be used when generating the new certificate; for example: -Template &quot;WebServer&quot;. The requested template must be installed on the CA. Note that the value entered must be the template name, not the template display name.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Describes what would happen if you executed the command without actually executing the command.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Request-CsCertificate** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

None. Instead, the **Request-CsCertificate** cmdlet helps manage instances of the Microsoft.Rtc.Management.Deployment.CertificateReference object.

</div>

<div>

## See Also


[Get-CsCertificate](get-cscertificate.md)  
[Import-CsCertificate](import-cscertificate.md)  
[Remove-CsCertificate](remove-cscertificate.md)  
[Set-CsCertificate](set-cscertificate.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

