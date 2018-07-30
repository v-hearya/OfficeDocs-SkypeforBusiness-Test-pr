---
title: Remove-CsConferenceDirectory
TOCTitle: Remove-CsConferenceDirectory
ms:assetid: c2c62a14-f3f3-472f-bf91-1fcea9e45425
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412961(v=OCS.15)
ms:contentKeyID: 48185335
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsConferenceDirectory

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Removes an existing conference directory. Conference directories are used to help dial-in conferencing users locate conference information. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsConferenceDirectory -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 deletes the conference directory with the Identity 2.

    Remove-CsConferenceDirectory -Identity 2

</div>

<div>

## EXAMPLE 2

Example 2 deletes all the conference directories found on the service UserServer:atl-cs-001.litwareinc.com. To do this, the command first calls the **Get-CsConferenceDirectory** cmdlet without any parameters; that returns a collection of all the conference directories currently in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those directories hosted on the service UserServer:atl-cs-001.litwareinc.com. In turn, that filtered collection is piped to, and deleted by, the **Remove-CsConferenceDirectory** cmdlet.

    Get-CsConferenceDirectory | Where-Object {$_.ServiceID -match "UserServer:atl-cs-001.litwareinc.com"} | Remove-CsConferenceDirectory

</div>

</div>

<div>

## Detailed Description

When you create a dial-in conferencing Uniform Resource Identifier (URI) those URIs are assigned unique SIP addresses. However, SIP addresses are difficult to translate to devices that are not SIP-aware; for example, a public switched telephone network (PSTN) telephone can’t translate a SIP address. Because of that, Lync Server uses conference directories as a way to help these devices locate, and connect to, dial-in conferences. This is done by creating a SIP conference directory that is associated with each dial-in conferencing URI, and is identified by an integer value rather than a SIP URI. PSTN telephones and other devices can then use these numbers (rather than a SIP URI) when connecting to conferences; the directory number is included in the PSTN conference identification users enter when connecting to a dial-in conference.

Conference directories are created by using the **New-CsConferenceDirectory** cmdlet. Occasionally, you might need to delete one or more of these directories; for example, you might need to decommission the pool where the directories were hosted. Conference directories can be removed by calling the **Remove-CsConferenceDirectory** cmdlet. Note that if you need to move a directory from one pool to another, you can do so by calling the **Move-CsConferenceDirectory** cmdlet.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsConferenceDirectory** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsConferenceDirectory"}

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
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Numeric identity of the conference directory to be removed.</p></td>
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
<td><p>When present, removes the conference directory even if the pool that hosts the directory is currently unavailable. By default, the <strong>Remove-CsConferenceDirectory</strong> cmdlet will not remove directories if the corresponding pool cannot be contacted.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.PstnConf.ConferenceDirectories object. The **Remove-CsConferenceDirectory** cmdlet accepts pipelined input of conference directory objects.

</div>

<div>

## Return Types

None. Instead, the **Removes-CsConferenceDirectory** cmdlet deletes instances of the Microsoft.Rtc.Management.WritableConfig.Settings.PstnConf.ConferenceDirectories object.

</div>

<div>

## See Also


[Get-CsConferenceDirectory](get-csconferencedirectory.md)  
[Move-CsConferenceDirectory](move-csconferencedirectory.md)  
[New-CsConferenceDirectory](new-csconferencedirectory.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

