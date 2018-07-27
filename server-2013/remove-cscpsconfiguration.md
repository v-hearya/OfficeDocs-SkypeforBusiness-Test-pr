---
title: Remove-CsCpsConfiguration
TOCTitle: Remove-CsCpsConfiguration
ms:assetid: 546343e1-a2e4-4bc0-bf6d-c8ae9bb3e690
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398358(v=OCS.15)
ms:contentKeyID: 48184134
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsCpsConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Removes an existing Call Park service configuration. Call parking is a service that allows a user to "park" an incoming phone call. Parking a call transfers it to a number in a specified range, or orbit, and then immediately places the call on hold. Anyone (not just the person who originally answered the call) can resume the conversation from any telephone simply by entering the correct number. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsCpsConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 uses the **Remove-CsCpsConfiguration** cmdlet to delete the Call Park service configuration with the Identity site:Redmond1. Because identities are unique, this command will result in only one configuration being deleted.

    Remove-CsCpsConfiguration -Identity site:Redmond1

</div>

<div>

## EXAMPLE 2

In Example 2, all the Call Park service configurations that have been defined at the site scope are deleted. To carry out this task, the command first uses the **Get-CsCpsConfiguration** cmdlet and the Filter parameter to return all the Call Park service configurations that have been defined at the site scope; the wildcard site:\* ensures that only settings that have an Identity that begins with the string value site: will be returned. This filtered collection is then piped to the **Remove-CsCpsConfiguration** cmdlet, which proceeds to delete each item in the collection. Note that any time you remove Call Park service settings from a site, the site will automatically begin to use the Call Park service settings configured at the global scope.

    Get-CsCpsConfiguration -Filter site:* | Remove-CsCpsConfiguration

</div>

</div>

<div>

## Detailed Description

This cmdlet is used to remove a Call Park service configuration. A Call Park service configuration specifies what happens to a call after it has been parked. For example, if a parked call isn’t answered after a period of time it can be automatically forwarded to someone else, such as an administrator, or to a Response Group. Calls can be configured to ring after a certain period of time to ensure the call isn’t forgotten. In addition, Call Park service can be configured to play music on hold to the caller while the call is parked.

This cmdlet can be used to remove any Call Park configurations, including the Global configuration. In the case of the Global configuration, however, the configuration will not actually be removed; instead, it will simply be reset to the default values.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsCpsConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsCpsConfiguration"}

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
<td><p>The unique identifier of the Call Park service configuration you want to remove. This identifier will be either Global or site:&lt;sitename&gt;, where &lt;sitename&gt; is the name of the site to which the configuration applies.</p></td>
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
<td><p>Suppresses any confirmation prompts that would otherwise be displayed before making changes.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.CallParkServiceSettings.CallParkServiceSettings object. Accepts pipelined input of Call Park service configuration objects.

</div>

<div>

## Return Types

Removes an object of type Microsoft.Rtc.Management.WritableConfig.Settings.CallParkServiceSettings.CallParkServiceSettings.

</div>

<div>

## See Also


[New-CsCpsConfiguration](new-cscpsconfiguration.md)  
[Set-CsCpsConfiguration](set-cscpsconfiguration.md)  
[Get-CsCpsConfiguration](get-cscpsconfiguration.md)  
[Set-CsCallParkServiceMusicOnHoldFile](set-cscallparkservicemusiconholdfile.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

