---
title: Remove-CsDialInConferencingConfiguration
TOCTitle: Remove-CsDialInConferencingConfiguration
ms:assetid: 0c7f2a69-eeed-41bf-8ba7-5cc36dfdfa3c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398174(v=OCS.15)
ms:contentKeyID: 48183393
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsDialInConferencingConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Removes one or more collections of dial-in conferencing configuration settings. These settings determine how Lync Server responds when users join or leave a dial-in conference. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsDialInConferencingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

In Example 1, the dial-in conferencing configuration settings for the Redmond site are deleted.

    Remove-CSDialInConferencingConfiguration -Identity "site:Redmond"

</div>

<div>

## EXAMPLE 2

In Example 2, all the dial-in conferencing settings that have been configured at the site scope are deleted. To do this, the command first uses the **Get-CSDialInConferencingConfiguration** cmdlet and the Filter parameter to return a collection of all the dial-in conferencing settings that have been configured at the site scope. (The filter value "site:\*" ensures that only settings that have an Identity that begins with the string value "site:" are returned.) This filtered collection is then piped to the **Remove-CSDialInConferencingConfiguration** cmdlet, which removes each item in the collection.

    Get-CSDialInConferencingConfiguration -Filter "site:*" | Remove-CSDialInConferencingConfiguration

</div>

<div>

## EXAMPLE 3

In Example 3, all the dial-in conferencing configuration settings that do not use name recording are deleted. To carry out this task, the command first calls the **Get-CSDialInConferencingConfiguration** cmdlet without any parameters in order to return a collection of all the dial-in conferencing configuration settings currently in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the EnableNameRecording property is equal to False. In turn, this filtered collection is piped to the **Remove-CSDialInConferencingConfiguration** cmdlet, which deletes each item in the collection.

    Get-CSDialInConferencingConfiguration | Where-Object {$_.EnableNameRecording -eq $False} | Remove-CSDialInConferencingConfiguration

</div>

</div>

<div>

## Detailed Description

When users join (or leave) a dial-in conference, Lync Server can respond in different ways. For example, participants might be asked to record their name before they can enter the conference itself. Likewise, administrators can decide whether they want to have Lync Server announce that dial-in participants have either left or joined a conference.

These conference "join behaviors" are managed using dial-in conferencing configuration settings; these settings can be configured at the global scope or at the site scope. (Settings configured at the site scope take precedence over settings configured at the global scope.) When you install Lync Server, a global collection of dial-in conferencing configuration settings will be created for you. If you want to have different settings for a site (or set of sites), you can create those collections by using the **New-CSDialInConferencingConfiguration** cmdlet.

The **Remove-CSDialInConferencingConfiguration** cmdlet deletes any dial-in conferencing settings that have been configured at the site scope. When these site-specific settings are deleted, users in the affected sites will have their dial-in conferencing behaviors governed by the global settings.

You can also run the **Remove-CSDialInConferencingConfiguration** cmdlet against the global dial-in conferencing settings. If you do that, the global settings will not be removed; that’s because the global settings cannot be removed. Instead, all the properties within that collection of settings will be reset to their default values.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsDialInConferencingConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsDialInConferencingConfiguration"}

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
<td><p>Indicates the Identity of the dial-in conferencing configuration settings to be removed. To refer to the global settings, use this syntax: -Identity global. To refer to site settings, use syntax similar to this: -Identity site:Redmond. Note that you cannot use wildcards when specifying an Identity.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.DialInConferencingSettings.DialInConferencingConfiguration object. The **Remove-CSDialInConferencingConfiguration** cmdlet accepts pipelined instances of the dial-in conferencing configuration object.

</div>

<div>

## Return Types

None. Instead, the **Remove-CSDialInConferencingConfiguration** cmdlet deletes instances of the Microsoft.Rtc.Management.WritableConfig.Settings.DialInConferencingSettings.DialInConferencingConfiguration object.

</div>

<div>

## See Also


[Get-CsDialInConferencingConfiguration](get-csdialinconferencingconfiguration.md)  
[New-CsDialInConferencingConfiguration](new-csdialinconferencingconfiguration.md)  
[Set-CsDialInConferencingConfiguration](set-csdialinconferencingconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

