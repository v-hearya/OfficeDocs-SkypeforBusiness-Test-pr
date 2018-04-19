---
title: Get-CsConferenceDisclaimer
TOCTitle: Get-CsConferenceDisclaimer
ms:assetid: 2382aaef-9c5e-43f8-99de-6c880134db7d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425714(v=OCS.15)
ms:contentKeyID: 48183633
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsConferenceDisclaimer

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Returns information about the conference disclaimer used in your organization. The conference disclaimer is a message that is displayed to users who join the conference by using a hyperlink (for example, users who paste a link to the conference into a browser such as Windows Internet Explorer). This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsConferenceDisclaimer [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsConferenceDisclaimer [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 returns information about the conference disclaimer configured for use in your organization. Because you are limited to a single disclaimer (configured at the global scope), you do not need to specify an Identity when running this command.

    Get-CSConferenceDisclaimer

</div>

</div>

<div>

## Detailed Description

When configuring conferencing settings, administrators can include a legal disclaimer to display to participants at the time participants join conferences hosted by Lync Server. This disclaimer is typically used to explain legal and intellectual property laws regarding the conference, and users cannot join the conference without agreeing to the stipulations set forth in the disclaimer. Note that this disclaimer is only shown to users who join a conference by using a hyperlink.

The **Get-CsConferenceDisclaimer** cmdlet enables you to view the body and header of your organization’s disclaimer.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsConferenceDisclaimer** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsConferenceDisclaimer"}

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
<td><p>Enables you to use wildcard values when referencing a conference disclaimer. Because you can only have a single, global instance of the conference disclaimer, there is really no reason to ever use the Filter parameter. However, you can use the following syntax to reference the global disclaimer: -Filter &quot;g*&quot;. That syntax brings back all the conference disclaimers that have an Identity that begins with the letter &quot;g&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Unique Identity of the conference disclaimer. Because you can only have a single, global instance of the conference disclaimer, you do not need to specify an Identity when calling the <strong>Get-CsConferenceDisclaimer</strong> cmdlet. You can, however, use the following syntax to reference the global disclaimer: -Identity global.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the conference disclaimer data from the local replica of the Central Management store rather than from the Central Management store itself.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None.

</div>

<div>

## Return Types

The **Get-CsConferenceDisclaimer** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConferenceDisclaimer object.

</div>

<div>

## See Also


[Remove-CsConferenceDisclaimer](remove-csconferencedisclaimer.md)  
[Set-CsConferenceDisclaimer](set-csconferencedisclaimer.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

