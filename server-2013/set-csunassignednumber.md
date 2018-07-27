---
title: Set-CsUnassignedNumber
TOCTitle: Set-CsUnassignedNumber
ms:assetid: e7f52423-58d1-410a-9071-731bde45d3d4
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg399033(v=OCS.15)
ms:contentKeyID: 48185882
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsUnassignedNumber

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-25_

Modifies an existing range of unassigned numbers and the routing rules that apply to those numbers. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsUnassignedNumber [-Identity <XdsGlobalRelativeIdentity>] [-Instance <PSObject>] [-NumberRangeEnd <String>] [-NumberRangeStart <String>] <COMMON PARAMETERS>

    Set-CsUnassignedNumber -ExUmAutoAttendantPhoneNumber <String> [-Identity <XdsGlobalRelativeIdentity>] [-Instance <PSObject>] [-NumberRangeEnd <String>] [-NumberRangeStart <String>] <COMMON PARAMETERS>

    Set-CsUnassignedNumber -AnnouncementName <String> -AnnouncementService <String> [-Identity <XdsGlobalRelativeIdentity>] [-Instance <PSObject>] [-NumberRangeEnd <String>] [-NumberRangeStart <String>] <COMMON PARAMETERS>

    Set-CsUnassignedNumber [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Priority <Int32>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example modifies the unassigned number range with the name UNSet1. We first pass the Identity parameter the value UNSet1, the name of the unassigned number range we want to modify. We then use the NumberRangeStart (+14255551000) and NumberRangeEnd (+14255551900) parameters to modify the range of unassigned numbers to which the specified announcement or Auto Attendant will apply.

    Set-CsUnassignedNumber -Identity UNSet1 -NumberRangeStart "+14255551000" -NumberRangeEnd "+14255551900"

</div>

<div>

## EXAMPLE 2

This example modifies the Announcement of all unassigned number range settings that currently have an Announcement with the string "Welcome" in the name. First we call the **Get-CsUnassignedNumber** cmdlet to retrieve all unassigned number settings. We pipe that collection of settings to the **Where-Object** cmdlet, which narrows down the collection to only those settings where the AnnouncementName property contains (-match) the string Welcome. Once we have those settings, we pipe them to the **Set-CsUnassignedNumber** cmdlet, where we modify the Application Server ID of the Announcement Service (ApplicationServer:redmond.litwareinc.com) with the AnnouncementService parameter and the name of the new announcement (Help Desk Announcement) with the AnnouncementName parameter. Note that even if the new Announcement has a different name but the same service ID, you must still specify the service ID along with the name.

    Get-CsUnassignedNumber | Where-Object {$_.AnnouncementName -match "Welcome"} | Set-CsUnassignedNumber -AnnouncementService ApplicationServer:redmond.litwareinc.com -AnnouncementName "Help Desk Announcement"

</div>

</div>

<div>

## Detailed Description

Unassigned numbers are phone numbers that have been assigned to an organization but that have not been assigned to specific users or phones. Lync Server can be set up to route calls to appropriate destinations when an unassigned number is called. This cmdlet modifies the settings that define that routing.

In order to modify some of the settings for this cmdlet, your system must already either have Announcements defined or an Exchange UM Auto Attendant set up. To determine whether you have Announcements, call the **Get-CsAnnouncement** cmdlet. To create a new Announcement, call the **New-CsAnnouncement** cmdlet. To check on Exchange UM Auto Attendant settings, run the **Get-CsExUmContact** cmdlet.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsUnassignedNumber** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsUnassignedNumber"}

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
<td><p><em>AnnouncementName</em></p></td>
<td><p>Required</p></td>
<td><p>String</p></td>
<td><p>The name of the Announcement that will be used to handle calls to this range of numbers.</p></td>
</tr>
<tr class="even">
<td><p><em>AnnouncementService</em></p></td>
<td><p>Required</p></td>
<td><p>String</p></td>
<td><p>The fully qualified domain name (FQDN) or service ID of the Announcement server.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExUmAutoAttendantPhoneNumber</em></p></td>
<td><p>Required</p></td>
<td><p>String</p></td>
<td><p>The phone number of the Exchange UM Auto Attendant to route calls in this range to. The Exchange UM Auto Attendant contact must already be set up in order to assign a value to this parameter.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suppresses any confirmation prompts that would otherwise be displayed before making changes.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>XdsGlobalRelativeIdentity</p></td>
<td><p>The unique name for the range of unassigned numbers being modified.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>Optional</p></td>
<td><p>DisplayAnnouncementVacantNumberRange</p></td>
<td><p>A reference to an object containing unassigned number settings. This object must be of type Microsoft.Rtc.Management.Voice.Helpers.DisplayAnnouncementVacantNumberRange and can be retrieved by calling the <strong>Get-CsUnassignedNumber</strong> cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>NumberRangeEnd</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The last number in the range of unassigned numbers. Must be greater than or equal to the number supplied for NumberRangeStart. To specify a range of one number, use the same number for the NumberRangeStart and NumberRangeEnd.</p>
<p>The number must match the regular expression (tel:)?(\+)?[1-9]\d{0,17}(;ext=[1-9]\d{0,9})?. This means the number may begin with the string tel: (if you don’t specify that string it will be automatically added for you), a plus sign (+), and a digit 1 through 9. The phone number can be up to 17 digits and may be followed by and extension in the format ;ext= followed by the extension number.</p></td>
</tr>
<tr class="odd">
<td><p><em>NumberRangeStart</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The first number in the range of unassigned numbers. Must be less than or equal to the value supplied for NumberRangeEnd.</p>
<p>The number must match the regular expression (tel:)?(\+)?[1-9]\d{0,17}(;ext=[1-9]\d{0,9})?. This means the number may begin with the string tel: (if you don’t specify that string it will be automatically added for you), a plus sign (+), and a digit 1 through 9. The phone number can be up to 17 digits and may be followed by an extension in the format ;ext= followed by the extension number.</p></td>
</tr>
<tr class="even">
<td><p><em>Priority</em></p></td>
<td><p>Optional</p></td>
<td><p>Int32</p></td>
<td><p>It is possible for unassigned number ranges to overlap. If a number falls within more than one range, the range with the highest priority will take effect.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Describes what would happen if you executed the command without actually executing the command.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

Microsoft.Rtc.Management.Voice.Helpers.DisplayAnnouncementVacantNumberRange object. Accepts pipelined input of unassigned number objects.

</div>

<div>

## Return Types

This cmdlet does not return a value. It modifies an object of type Microsoft.Rtc.Management.Voice.Helpers.DisplayAnnouncementVacantNumberRange.

</div>

<div>

## See Also


[New-CsUnassignedNumber](new-csunassignednumber.md)  
[Remove-CsUnassignedNumber](remove-csunassignednumber.md)  
[Get-CsUnassignedNumber](get-csunassignednumber.md)  
[New-CsAnnouncement](new-csannouncement.md)  
[Get-CsAnnouncement](get-csannouncement.md)  
[Get-CsExUmContact](get-csexumcontact.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

