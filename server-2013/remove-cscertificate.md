---
title: Remove-CsCertificate
TOCTitle: Remove-CsCertificate
ms:assetid: b7a83a58-9d3f-458a-867e-44466c9817dc
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412895(v=OCS.15)
ms:contentKeyID: 48185199
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsCertificate

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Removes a certificate previously marked as being available for use by Lync Server. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsCertificate -Type <CertType[]> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Identity <XdsIdentity>] [-Previous <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 deletes all the WebServicesExternal certificates available to Lync Server. If any of these certificates are currently being used, the **Remove-CsCertificate** cmdlet will ask you if you are sure you want to remove the certificate; you must respond to that prompt before the command can complete. To bypass the confirmation prompt, use the Force parameter:

Remove-CsCertificate –Type WebServicesExternal -Force

    Remove-CsCertificate -Type WebServicesExternal

</div>

</div>

<div>

## Detailed Description

Lync Server uses certificates as a way for servers and server roles to verify their identities; for example, an Edge Server uses certificates to verify that the computer it is communicating with really is a Front End Server, and vice versa. In order to fully implement Lync Server, you will need to have the appropriate certificates assigned to the appropriate server roles.

The **Remove-CsCertificate** cmdlet provides a way for you to remove certificates currently in use by Lync Server. The **Remove-CsCertificate** cmdlet does not actually delete the certificate itself; instead, it marks the certificate as no longer being available for use by Lync Server, removes any certificate bindings, and revokes access permissions to the certificate (assuming no other service is using the certificate). Among other things, this means that the certificate will no longer appear when you run the **Get-CsCertificate** cmdlet.

To again use the certificate with Lync Server you will need to reassign the certificate to Lync Server by using the **Set-CsCertificate** cmdlet.

If you try to remove a certificate that is currently in use, the **Remove-CsCertificate** cmdlet will be ask if you are sure that you want to remove the certificate; the certificate cannot be removed until you respond to that prompt. To bypass the prompt, and silently delete a certificate even if it is currently in use, add the Force parameter to your command:

Remove-CsCertificate –Type WebServicesExternal -Force

Who can run this cmdlet: You must be a local administrator and a member of the domain in order to run the **Remove-CsCertificate** cmdlet locally. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsCertificate"}

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
<td><p><em>Type</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.CertType[]</p></td>
<td><p>Type of certificate to be deleted. Certificate types include (but are not limited to):</p>
<p>AccessEdgeExternal</p>
<p>AudioVideoAuthentication</p>
<p>DataEdgeExternal</p>
<p>Default</p>
<p>External</p>
<p>Internal</p>
<p>PICWebService (Microsoft Lync Online 2010 only)</p>
<p>ProvisionService (Microsoft Lync Online 2010 only)</p>
<p>WebServicesExternal</p>
<p>WebServicesInternal</p>
<p>WsFedTokenTransfer</p>
<p>For example, this syntax deletes the Default certificate: -Type Default.</p>
<p>You can delete multiple types in a single command by separating the certificate types with commas:</p>
<p>-Type Internal,External,Default</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Bypasses the confirmation prompt that typically occurs if you attempt to delete a certificate that is currently in use.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>When set to Global, removes the certificate from the global scope. When not specified, certificates are removed from the local computer.</p></td>
</tr>
<tr class="odd">
<td><p><em>Previous</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>When specified, removes the previously-assigned certificate instead of the currently-assigned certificate.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to record detailed information about the procedures carried out by the <strong>Remove-CsCertificate</strong> cmdlet. The parameter value should be the full path to the HTML file to be generated; for example: -Report C:\Logs\Certificates.html. If the specified file already exists it will automatically be overwritten with the new information.</p></td>
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

None. The Remove-CsCertificate cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

None. Instead, the **Remove-CsCertificate** cmdlet deletes instances of the Microsoft.Rtc.Management.Deployment.CertificateReference object.

</div>

<div>

## See Also


[Get-CsCertificate](get-cscertificate.md)  
[Import-CsCertificate](import-cscertificate.md)  
[Request-CsCertificate](request-cscertificate.md)  
[Set-CsCertificate](set-cscertificate.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

