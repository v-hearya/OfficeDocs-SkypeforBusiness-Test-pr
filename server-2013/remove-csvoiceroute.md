---
title: Remove-CsVoiceRoute
TOCTitle: Remove-CsVoiceRoute
ms:assetid: 6687e538-e8f6-4bf0-b393-2c7b4a3f2f06
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398468(v=OCS.15)
ms:contentKeyID: 48184337
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsVoiceRoute

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Removes a voice route. Voice routes contain instructions that tell Lync Server how to route calls from Enterprise Voice users to phone numbers on the public switched telephone network (PSTN) or a private branch exchange (PBX). This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsVoiceRoute -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Removes the settings for the voice route with the identity Route1.

    Remove-CsVoiceRoute -Identity Route1

</div>

<div>

## EXAMPLE 2

This command removes all voice routes from the organization. First all voice routes are retrieved by the **Get-CsVoiceRoute** cmdlet. These voice routes are then piped to the **Remove-CsVoiceRoute** cmdlet, which removes each one.

    Get-CsVoiceRoute | Remove-CsVoiceRoute

</div>

<div>

## EXAMPLE 3

This command removes all voice routes with an identity that includes the string "Redmond." First the **Get-CsVoiceRoute** cmdlet is called with the Filter parameter. The value of the Filter parameter is the string Redmond surrounded by wildcard characters (\*), which specifies that the string can be anywhere within the Identity. After all of the voice routes with identities that include the string Redmond are retrieved, these voice routes are piped to the **Remove-CsVoiceRoute** cmdlet, which removes each one.

    Get-CsVoiceRoute -Filter *Redmond* | Remove-CsVoiceRoute

</div>

</div>

<div>

## Detailed Description

Use this cmdlet to remove an existing voice route. Voice routes are associated with voice policies through PSTN usages, so removing a voice route does not change any values relating to a voice policy, it simply changes the routing for the numbers that had matched the pattern for the deleted voice route.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsVoiceRoute** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsVoiceRoute"}

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
<td><p>A string that uniquely identifies the voice route you want to delete. (If the route name contains a space, such as Test Route, you must enclose the full string in double quotes.)</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route object. Accepts pipelined input of voice route objects.

</div>

<div>

## Return Types

Removes an object of type Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route.

</div>

<div>

## See Also


[New-CsVoiceRoute](new-csvoiceroute.md)  
[Set-CsVoiceRoute](set-csvoiceroute.md)  
[Get-CsVoiceRoute](get-csvoiceroute.md)  
[Test-CsVoiceRoute](test-csvoiceroute.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

