---
title: Import-CsCertificate
TOCTitle: Import-CsCertificate
ms:assetid: 87bdafce-f4b9-4c44-ad8f-86c2deb680a4
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398688(v=OCS.15)
ms:contentKeyID: 48184723
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Import-CsCertificate

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Imports a certificate for use with Lync Server. If a certificate is not acquired by using the **Request-CsCertificate** cmdlet, then that certificate must be imported before it can be assigned to a Lync Server server role. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Import-CsCertificate -Identity <XdsIdentity> -Type <CertType[]> <COMMON PARAMETERS>

    Import-CsCertificate [-PrivateKeyExportable <$true | $false>] <COMMON PARAMETERS>

    COMMON PARAMETERS: -Path <String> [-Confirm [<SwitchParameter>]] [-EffectiveDate <DateTime>] [-Force <SwitchParameter>] [-Password <String>] [-Report <String>] [-Roll <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 imports the certificate C:\\Certificates\\WebServer.pfx. After the command completes, the certificate will be available to be assigned to a server role.

    Import-CsCertificate -Path "C:\Certificates\WebServer.pfx" -PrivateKeyExportable $True

</div>

</div>

<div>

## Detailed Description

Lync Server uses certificates as a way for servers and server roles to verify their identities; for example, an Edge Server uses certificates to verify that the computer it is communicating with really is a Front End Server and vice versa. In order to fully implement Lync Server you will need to have the appropriate certificates assigned to the appropriate server roles.

In order for certificates to be assigned to a Lync Server role those certificates must be made known to Lync Server. The **Request-CsCertificate** cmdlet enables you to make both online and offline requests for new certificates. If an online request is made, the certificate will automatically be downloaded and saved in the local certificate store; equally important, it will be immediately available for use by Lync Server. If an offline request is made, a certificate file will be sent to you. At that point, you can use the **Import-CsCertificate** cmdlet to import the certificate, a process that makes the certificate available for assignment to a Lync Server server role.

Who can run this cmdlet: You must be a local administrator in order to run the **Import-CsCertificate** cmdlet locally. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Import-CsCertificate"}

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
<td><p><em>Identity</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>When set to Global, enables the certificate to function at the global scope. Global certificates will automatically be copied and distributed to the appropriate computers.</p></td>
</tr>
<tr class="even">
<td><p><em>Path</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Full path to the certificate file to be imported. For example: –Path &quot;C:\Certificates\WebServer.cer&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><em>Type</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.CertType[]</p></td>
<td><p>Type of certificate being requested. Certificate types include, but are not limited to, the following:</p>
<p>* AccessEdgeExternal</p>
<p>* AudioVideoAuthentication</p>
<p>* DataEdgeExternal</p>
<p>* Default</p>
<p>* External</p>
<p>* Internal</p>
<p>* iPadAPNService</p>
<p>* iPhoneAPNService</p>
<p>* LogRetentionService</p>
<p>* MPNService</p>
<p>* OAuthTokenIssuer</p>
<p>* PICWebService</p>
<p>* ProvisionService</p>
<p>* SMPDNSWebService</p>
<p>* TenantAdmin</p>
<p>* UpgradeEngineService</p>
<p>* WebServicesExternal</p>
<p>* WebServicesInternal</p>
<p>* WsFedTokenTransfer</p>
<p>* XMPPServer</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>EffectiveDate</em></p></td>
<td><p>Optional</p></td>
<td><p>System.DateTime</p></td>
<td><p>Date and time when the certificate can first be used. For example, to configure a certificate for first use at 8:00 AM on July 31, 2012 use this syntax on a server running under the US English Region and Language settings:</p>
<p>-EffectiveTime &quot;7/31/2012 8:00 AM&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Password</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Password associated with the certificate file.</p></td>
</tr>
<tr class="even">
<td><p><em>PrivateKeyExportable</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>When set to True, ensures that the private key portion of the certificate can be read by the Network Service account.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report &quot;C:\Logs\Certificates.html&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Roll</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Enables you to update the specified certificate at the date and time specified by the EffectiveDate parameter; this enables you to specify a date and time when the new certificate will become the primary certificate. Note that your command will fail if you specify the Roll parameter without including the EffectiveDate parameter.</p></td>
</tr>
<tr class="odd">
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

None. The **Import-CsCertificate** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

None.

</div>

<div>

## See Also


[Get-CsCertificate](get-cscertificate.md)  
[Remove-CsCertificate](remove-cscertificate.md)  
[Request-CsCertificate](request-cscertificate.md)  
[Set-CsCertificate](set-cscertificate.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

