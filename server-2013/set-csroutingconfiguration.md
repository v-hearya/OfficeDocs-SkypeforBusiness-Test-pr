---
title: Set-CsRoutingConfiguration
TOCTitle: Set-CsRoutingConfiguration
ms:assetid: ab69c6e8-262a-4ecb-b1af-513383c494fe
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412811(v=OCS.15)
ms:contentKeyID: 48185110
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsRoutingConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-25_

Modifies a list of voice routes. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsRoutingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsRoutingConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-EnableLocationBasedRouting <$true | $false>] [-Force <SwitchParameter>] [-Route <PSListModifier>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

It takes several steps to modify a voice route within a routing configuration. In this example, we start by retrieving the routing configuration object by calling the **Get-CsRoutingConfiguration** cmdlet. We assign the object retrieved (there will be only one) to the variable $a.

In line 2 of this example we retrieve the contents of the Route property from variable $a, which is a collection of voice route objects. We then pipe that collection to the **Where-Object** cmdlet, where we search the collection for all voice route objects with a Name matching the string LocalRoute. We assign that object to the variable $b.

Next, we modify the LocalRoute voice route object by assigning the value $False to the property SuppressCallerId. By updating that object we’ve updated the object in variable $a. However, that object is still only in memory. As a final step, we need to save those changes by passing $a to the Instance parameter of the **Set-CsRoutingConfiguration** cmdlet.

This is not the recommended way of modifying a routing configuration. To modify a routing configuration, simply change the individual voice routes with the **Set-CsVoiceRoute** cmdlet, as shown here:

Set-CsVoiceRoute -Identity LocalRoute -SuppressCallerId $False

That one line will accomplish the same task shown in Example 1.

    $a = Get-CsRoutingConfiguration
    $b = $a.Route | Where-Object {$_.Name -match "LocalRoute"}
    $b.SuppressCallerId = $False
    Set-CsRoutingConfiguration -Instance $a

</div>

</div>

<div>

## Detailed Description

Voice routes contain instructions that tell Lync Server how to route calls from Enterprise Voice users to phone numbers on the public switched telephone network (PSTN) or a private branch exchange (PBX). With this cmdlet you can modify the settings of any voice route defined within a Lync Server deployment.

The use of this cmdlet is not recommended. To modify routing configurations, modify the individual voice routes by calling the **Set-CsVoiceRoute** cmdlet.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsRoutingConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsRoutingConfiguration"}

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
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableLocationBasedRouting</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>When set to True, voice routing will be managed by taking into account the location of both the user placing the call and the user receiving the call. The default value is False.</p></td>
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
<td><p>XdsIdentity</p></td>
<td><p>The scope of the routing configuration. This must be Global.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>Optional</p></td>
<td><p>PstnRoutingSettings</p></td>
<td><p>A routing configuration (Microsoft.Rtc.Management.WritablConfig.Policy.Voice.PstnRoutingSettings) object. An object of this type can be retrieved by calling the <strong>Get-CsRoutingConfiguration</strong> cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>Route</em></p></td>
<td><p>Optional</p></td>
<td><p>PSListModifier</p></td>
<td><p>A list of all voice routes (Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route objects) defined for the Lync Server deployment.</p>
<p>You should modify individual voice route objects by using the <strong>Set-CsVoiceRoute</strong> cmdlet. That is the recommended way of modifying routes in this list.</p></td>
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

Microsoft.Rtc.WritableConfig.Management.Policy.Voice.PSTNRoutingSettings object. Accepts pipelined input of a routing configuration object.

</div>

<div>

## Return Types

The **Set-CsRoutingConfiguration** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.PstnRoutingSettings object.

</div>

<div>

## See Also


[New-CsRoutingConfiguration](new-csroutingconfiguration.md)  
[Remove-CsRoutingConfiguration](remove-csroutingconfiguration.md)  
[Get-CsRoutingConfiguration](get-csroutingconfiguration.md)  
[Set-CsVoiceRoute](set-csvoiceroute.md)  
[Get-CsVoiceRoute](get-csvoiceroute.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

