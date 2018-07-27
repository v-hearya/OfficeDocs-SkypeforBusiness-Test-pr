---
title: Set-CsCertificate
TOCTitle: Set-CsCertificate
ms:assetid: 6da0be05-b257-4258-9d6d-7ddf283f1038
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398518(v=OCS.15)
ms:contentKeyID: 48184432
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsCertificate

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-07_

Enables you to assign a certificate to a Lync Server server or server role. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsCertificate -Reference <CertificateReference> -Type <CertType[]> [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsCertificate -Identity <XdsIdentity> -Path <String> -Type <CertType[]> [-Password <String>] <COMMON PARAMETERS>

    Set-CsCertificate -Thumbprint <String> -Type <CertType[]> [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-EffectiveDate <DateTime>] [-Force <SwitchParameter>] [-Report <String>] [-Roll <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 assigns the certificate with the Thumbprint B142918E463981A76503828BB1278391B716280987B to the WebServicesExternal role on the local computer.

    Set-CsCertificate -Type WebServicesExternal -Thumbprint "B142918E463981A76503828BB1278391B716280987B"

</div>

<div>

## EXAMPLE 2

Example 2 assigns the assigns the certificate with the Thumbprint B142918E463981A76503828BB1278391B716280987B to three different roles on the local computer: Default, WebServicesInternal, and WebServicesExternal.

    Set-CsCertificate -Type Default, WebServicesInternal, WebServicesExternal -Thumbprint "B142918E463981A76503828BB1278391B716280987B"

</div>

</div>

<div>

## Detailed Description

Lync Server uses certificates as a way for servers and server roles to verify their identities; for example, an Edge Server uses certificates to verify that the computer it is communicating with really is a Front End Server and vice versa. In order to fully implement Lync Server, you will need to have the appropriate certificates assigned to the appropriate server roles.

The **Set-CsCertificate** cmdlet enables administrators to assign a certificate to a server or server role. Note that you can only assign certificates that have already been configured for use with Lync Server. To identify certificates available for assignment, use the **Get-CsCertificate** cmdlet.

Who can run this cmdlet: You must be a local administrator in order to run the **Set-CsCertificate** cmdlet locally. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsCertificate"}

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
<td><p>Full path to the .PFX certificate file.</p></td>
</tr>
<tr class="odd">
<td><p><em>Reference</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.CertificateReference</p></td>
<td><p>Object reference to a certificate configured for use with Lync Server. The following command returns an object reference (the variable $x) representing a certificate with the thumbprint B142918E463981A76503828BB1278391B716280987B:</p>
<p>$x = Get-CsCertificate | Where-Object {$_.Thumbprint –eq &quot;B142918E463981A76503828BB1278391B716280987B&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Thumbprint</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Unique identifier for the certificate. A certificate thumbprint looks similar to this: B142918E463981A76503828BB1278391B716280987B.</p></td>
</tr>
<tr class="odd">
<td><p><em>Type</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.CertType[]</p></td>
<td><p>Type of certificate being assigned. Certificate types include, but are not limited to, the following:</p>
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
<p>For example, this syntax assigns the Default certificate: -Type Default.</p>
<p>You can specify multiple types in a single command by separating the certificate types with commas:</p>
<p>-Type Internal,External,Default</p></td>
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
<td><p>Suppresses the display of any non-fatal error message that might arise when running the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Password</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Password for the certificate.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to record detailed information about the procedures carried out by the <strong>Set-CsCertificate</strong> cmdlet. The parameter value should be the full path to the HTML file to be generated; for example: -Report C:\Logs\Certificates.html. If the specified file already exists it will automatically be overwritten with the new information.</p></td>
</tr>
<tr class="odd">
<td><p><em>Roll</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Enables you to update the specified certificate at the date and time specified by the EffectiveDate parameter; this enables you to specify a date and time when the new certificate will become the primary certificate. Note that your command will fail if you specify the Roll parameter without including the EffectiveDate parameter.</p></td>
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

Microsoft.Rtc.Management.Deployment.CertificateReference.

</div>

<div>

## Return Types

The **Set-CsCertificate** cmdlet does not return any values or objects.

</div>

<div>

## See Also


[Get-CsCertificate](get-cscertificate.md)  
[Import-CsCertificate](import-cscertificate.md)  
[Remove-CsCertificate](remove-cscertificate.md)  
[Request-CsCertificate](request-cscertificate.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

