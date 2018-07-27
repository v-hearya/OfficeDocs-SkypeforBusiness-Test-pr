---
title: Get-CsConferenceDirectory
TOCTitle: Get-CsConferenceDirectory
ms:assetid: 2b7927ab-c6b3-42ce-9c27-9825cd47fd77
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425771(v=OCS.15)
ms:contentKeyID: 48183718
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsConferenceDirectory

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Returns information about the conference directories configured for use in your organization. Conference directories are used to help dial-in conferencing users locate conference information. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsConferenceDirectory [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsConferenceDirectory [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 returns information about all the conference directories configured for use in your organization.

    Get-CsConferenceDirectory

</div>

<div>

## EXAMPLE 2

Example 2 returns information about the conference directory with the Identity 2. Because identities must be unique this command will never return more than a single conference directory.

    Get-CsConferenceDirectory -Identity 2

</div>

<div>

## EXAMPLE 3

Example 3 returns all the conference directories housed on the service UserServer:atl-cs-001.litwareinc.com. To do this, the command first calls the **Get-CsConferenceDirectory** cmdlet without any parameters in order to return a collection of all the conference directories found in your organization. This collection is then piped to the **Where-Object** cmdlet, which selects only those directories where the ServiceID matches the string value "UserServer:atl-cs-001.litwareinc.com".

    Get-CsConferenceDirectory | Where-Object {$_.ServiceID -match "UserServer:atl-cs-001.litwareinc.com"}

</div>

</div>

<div>

## Detailed Description

When you create a dial-in conferencing Uniform Resource Identifier (URI), those URIs are assigned unique SIP addresses. However, SIP addresses are difficult for devices that are not SIP-aware to translate; for example, a public switched telephone network (PSTN) telephone can’t translate a SIP address. Because of that, Lync Server uses conference directories as a way to help these devices locate, and connect to, dial-in conferences. This is done by creating a SIP conference directory that is associated with each dial-in conferencing URI, and is identified by an integer value rather than a SIP URI. PSTN telephones and other devices can use these numbers (rather than a SIP URI) when connecting to conferences; the directory number is included in the PSTN conference identification users enter when connecting to a dial-in conference.

The **Get-CsConferenceDirectory** cmdlet enables you to return information about all the conference directories configured for use in your organization.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsConferenceDirectory** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsConferenceDirectory"}

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
<td><p><em>Filter</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to use wildcards to specify the Identity of the conference directory (or directories) to be retrieved. Because directory Identities are numeric, this parameter might be of minimal value. However, this syntax will return all the conference directories that have an Identity that begins with the number 3: -Filter &quot;3*&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Numeric identifier (for example, 7) of the conference directory to be returned. If this parameter is omitted, then the <strong>Get-CsConferenceDirectory</strong> cmdlet returns information about all the conference directories in use in your organization.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the conference directory data from the local replica of the Central Management store rather than from the Central Management store itself.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Get-CsConferenceDirectory** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Get-CsConferenceDirectory** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.PstnConf.ConferenceDirectories object.

</div>

<div>

## See Also


[Move-CsConferenceDirectory](move-csconferencedirectory.md)  
[New-CsConferenceDirectory](new-csconferencedirectory.md)  
[Remove-CsConferenceDirectory](remove-csconferencedirectory.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

