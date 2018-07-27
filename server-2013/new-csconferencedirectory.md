---
title: New-CsConferenceDirectory
TOCTitle: New-CsConferenceDirectory
ms:assetid: fd5a4369-10cd-4337-94df-51bcaee4fde9
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg413080(v=OCS.15)
ms:contentKeyID: 48185958
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsConferenceDirectory

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Creates a new conference directory for use in your organization. Conference directories are used to help dial-in conferencing users locate conference information. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    New-CsConferenceDirectory -HomePool <String> -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Creates a new conference directory with the Identity 42. This directory will be hosted on the pool atl-cs-001.litwareinc.com.

    New-CsConferenceDirectory -Identity 42 -HomePool "atl-cs-001.litwareinc.com"

</div>

</div>

<div>

## Detailed Description

When you create a dial-in conferencing Uniform Resource Identifier (URI), those URIs are assigned unique SIP addresses. However, SIP addresses are difficult to translate to devices that are not SIP-aware; for example, a public switched telephone network (PSTN) telephone can’t translate a SIP address. Because of that, Lync Server uses conference directories as a way to help these devices locate, and connect to, dial-in conferences. This is done by creating a SIP conference directory that is associated with each dial-in conferencing URI, and is identified by an integer value rather than a SIP URI. PSTN telephones and other devices can then use these numbers (rather than a SIP URI) when connecting to conferences; the directory number is included in the PSTN conference identification users enter when connecting to a dial-in conference.

New conference directories can be created by calling the **New-CsConferenceDirectory** cmdlet.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsConferenceDirectory** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsConferenceDirectory"}

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
<td><p><em>HomePool</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Fully qualified domain name (FQDN) of the Registrar pool where the new conference directory will be hosted. For example: -Identity atl-cs-001.litwareinc.com.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Unique numeric identifier for the new conference directory. Identities can be any integer value between 0 and 9999 inclusive; however, Identities must be unique. (For example, you cannot have two directories with the Identity 575.) You do not need to follow a numeric order when creating new directories. For example, you can create a directory with the Identity 999 followed by a directory with the Identity 2 followed by a directory with the Identity 438, and so on.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
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

None. The **New-CsConferenceDirectory** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

Creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.PstnConf.ConferenceDirectories object.

</div>

<div>

## See Also


[Get-CsConferenceDirectory](get-csconferencedirectory.md)  
[Move-CsConferenceDirectory](move-csconferencedirectory.md)  
[Remove-CsConferenceDirectory](remove-csconferencedirectory.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

