---
title: Remove-CsConferenceDisclaimer
TOCTitle: Remove-CsConferenceDisclaimer
ms:assetid: 196252a1-2526-4944-9064-01d1846f3266
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398243(v=OCS.15)
ms:contentKeyID: 48183521
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsConferenceDisclaimer

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Clears the text from the header and body of the conference disclaimer used in your organization. The conference disclaimer is a message that is displayed to users who join the conference by using a hyperlink (for example, users who paste a link to the conference into a browser such as Windows Internet Explorer). This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsConferenceDisclaimer -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 resets the property values of the global disclaimer. That means that both the disclaimer Header and Body will be set to null values, giving you a blank disclaimer.

    Remove-CsConferenceDisclaimer -Identity global

</div>

</div>

<div>

## Detailed Description

When configuring conferencing settings, administrators can include a legal disclaimer to display to participants when these people join conferences hosted by Lync Server. This disclaimer is typically used to explain legal and intellectual property laws regarding the conference. Users cannot join the conference without agreeing to the stipulations set forth in the disclaimer. Note that this disclaimer is only shown to users who join a conference by using a hyperlink.

Lync Server allows for a single, global instance of the conference disclaimer. The **Remove-CsConferenceDisclaimer** cmdlet enables you to reset your conference disclaimer: when you run this cmdlet, both the disclaimer header and the disclaimer body are set to null values.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsConferenceDisclaimer** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsConferenceDisclaimer"}

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
<td><p>Unique Identity of the conference disclaimer to be removed. Although you can only have a single, global instance of the conference disclaimer, you must still use the Identity parameter when calling the <strong>Remove-CsConferenceDisclaimer</strong> cmdlet.</p></td>
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
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConferenceDisclaimer object. The **Remove-CsConferenceDisclaimer** cmdlet accepts pipelined input of conference disclaimer objects.

</div>

<div>

## Return Types

None. Instead, the **Remove-CsConferenceDisclaimer** cmdlet resets existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConferenceDisclaimer object to their default property values.

</div>

<div>

## See Also


[Get-CsConferenceDisclaimer](get-csconferencedisclaimer.md)  
[Set-CsConferenceDisclaimer](set-csconferencedisclaimer.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

