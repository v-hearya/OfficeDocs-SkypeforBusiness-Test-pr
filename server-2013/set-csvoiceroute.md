---
title: Set-CsVoiceRoute
TOCTitle: Set-CsVoiceRoute
ms:assetid: b786aec0-946e-4ce5-812e-25e5d8cfa4d5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412893(v=OCS.15)
ms:contentKeyID: 48185198
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsVoiceRoute

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Modifies a voice route. Voice routes contain instructions that tell Lync Server how to route calls from Enterprise Voice users to phone numbers on the public switched telephone network (PSTN) or a private branch exchange (PBX). This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsVoiceRoute [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsVoiceRoute [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AlternateCallerId <String>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-NumberPattern <String>] [-Priority <Int32>] [-PstnGatewayList <PSListModifier>] [-PstnUsages <PSListModifier>] [-SuppressCallerId <$true | $false>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This command sets the Description of the Route1 voice route to "Test Route."

    Set-CsVoiceRoute -Identity Route1 -Description "Test Route"

</div>

<div>

## EXAMPLE 2

The command in this example modifies the voice route with the identity Route1 to add the PSTN usage Long Distance to the list of usages for this voice route. Long Distance must be in the list of global PSTN usages (which can be retrieved with a call to the **Get-CsPstnUsage** cmdlet).

    Set-CsVoiceRoute -Identity Route1 -PstnUsages @{add="Long Distance"}

</div>

<div>

## EXAMPLE 3

This example modifies the voice route named Route1 to populate that route’s list of PSTN usages with all the existing usages for the organization. The first command in this example retrieves the list of global PSTN usages. Notice that the call to the **Get-CsPstnUsage** cmdlet is in parentheses; this means that we first retrieve an object containing PSTN usage information. (Because there is only one--global--PSTN usage, only one object will be retrieved.) The command then retrieves the Usage property of this object. That property, which contains a list of PSTN usages, is assigned to the variable $x. In the second line of this example, the **Set-CsVoiceRoute** cmdlet is called to modify the voice route with the identity Route1. Notice the value passed to the PstnUsages parameter: @{replace=$x}. This value says to replace everything in the PstnUsages list for this route with the contents of $x, which contain the PSTN usages list retrieved in line 1.

    $x = (Get-CsPstnUsage).Usage
    Set-CsVoiceRoute -Identity Route1 -PstnUsages @{replace=$x}

</div>

<div>

## EXAMPLE 4

This set of commands changes the Name property of the voice route with the identity Route1 to RouteA. Changing the Name property automatically changes the Identity property, in this case to RouteA.

In the first line, the **Get-CsVoiceRoute** cmdlet is called to retrieve the voice route with the identity Route1. The returned object is stored in the variable $x. Next, the Name property of that object is assigned the string value "RouteA". Finally, the object (contained in the variable $x) is passed to the Instance parameter of the **Set-CsVoiceRoute** cmdlet to make the change.

    $x = Get-CsVoiceRoute -Identity Route1
    $x.Name = "RouteA"
    Set-CsVoiceRoute -Instance $x

</div>

<div>

## EXAMPLE 5

This example modifies the voice route named Route1 and populates that route’s list of PSTN gateways (PstnGatewayList) with the server role of the gateway with the identity PstnGateway:192.168.0.100. In the first line of this example, the **Get-CsVoiceRoute** cmdlet is called to retrieve the voice route we want to modify, in this case Route1. Next we call the Add method on the PstnGatewayList property of Route1. We pass the Add method the Identity of the service we want to add. Finally, we call the **Set-CsVoiceRoute** cmdlet, passing the Instance parameter the variable $y, which will update Route1 (stored in $y) with the newly-added PSTN gateway.

    $y = Get-CsVoiceRoute -Identity Route1
    $y.PstnGatewayList.Add("PstnGateway:192.168.0.100")
    Set-CsVoiceRoute -Instance $y

</div>

</div>

<div>

## Detailed Description

Use this cmdlet to modify an existing voice route. Voice routes are associated with voice policies through public switched telephone network (PSTN) usages. A voice route includes a regular expression that identifies which phone numbers will be routed through a given voice route: phone numbers matching the regular expression will be routed through this route.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsVoiceRoute** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsVoiceRoute"}

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
<td><p><em>AlternateCallerId</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>If the SuppressCallerId parameter is set to True, the value of the AlternateCallerId parameter will be displayed to receiving parties rather than the caller’s actual number. This number should be a valid number and could be used to represent a division within an organization, such as Support or Human Resources.</p>
<p>If the SuppressCallerId parameter is set to False, the AlternateCallerId parameter is ignored.</p>
<p>This value must match the regular expression (\+)?[1-9]\d*(;ext=[1-9]\d*)?. In other words, the value can begin with a plus sign (+) but doesn’t need to; must consist of any number of digits; and may be followed by an extension that begins with ;ext= followed by any number of digits. (Note that if you include an extension the string must be placed within double quotes.)</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>A description of what this phone route is for.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses any confirmation prompts that would otherwise be displayed before making changes.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>The unique identity of the voice route. (If the route name contains a space, such as Test Route, you must enclose the full string in parentheses.)</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Optional</p></td>
<td><p>Route</p></td>
<td><p>Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values. This object must be of type Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route and can be retrieved by calling the <strong>Get-CsVoiceRoute</strong> cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><em>NumberPattern</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>A regular expression that specifies the phone numbers to which this route applies. Numbers matching this pattern will be routed according to the rest of the routing settings. For example, the default number pattern, [0-9]{10}, specifies a 10-digit number containing any digits 0 through 9.</p></td>
</tr>
<tr class="even">
<td><p><em>Priority</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Int32</p></td>
<td><p>A number could resolve to multiple voice routes. The priority determines the order in which the routes will be applied if more than one route is possible.</p></td>
</tr>
<tr class="odd">
<td><p><em>PstnGatewayList</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>A Mediation Server can be associated with multiple gateways. This parameter contains a list of gateways associated with this voice route. Each member of this list must be the service Identity of the PSTN gateway or Mediation Server. The value can refer to a Mediation Server only if the Mediation Server is configured for Microsoft Office Communications Server 2007 or Microsoft Office Communications Server 2007 R2. For Lync Server a PSTN gateway must be used. The service Identity is a string in the format ServiceRole:FQDN, where ServiceRole is the name of the service role (PSTNGateway), and FQDN is the fully qualified domain name (FQDN) of the pool or the IP address of the server. For example, PSTNGateway:redmondpool.litwareinc.com. Service identities can be retrieved by calling the command Get-CsService | Select-Object Identity.</p>
<p>If you make changes to a voice route and leave the PstnGatewayList list empty, or if the change you make removes all the items in the list, you’ll receive a warning message that users will be unable to make PSTN calls.</p></td>
</tr>
<tr class="even">
<td><p><em>PstnUsages</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>A list of PSTN usages (such as Local or Long Distance) that can be applied to this voice route. The PSTN usage must be an existing usage. (PSTN usages can be retrieved by calling the <strong>Get-CsPstnUsage</strong> cmdlet.)</p>
<p>If you make changes to a voice route and leave the PstnUsages list empty, or if the change you make removes all the PSTN usages in the list, you’ll receive a warning message that users will be unable to make PSTN calls.</p></td>
</tr>
<tr class="odd">
<td><p><em>SuppressCallerId</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Determines whether a caller’s ID will be revealed on outbound calls. If this parameter is set to True, caller ID will be suppressed. In place of the actual ID, the value of the AlternateCallerId will be displayed. When SuppressCallerId is set to True, a value for AlternateCallerId must be supplied.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route object. The **Set-CsVoiceRoute** cmdlet accepts pipelined input of voice route objects.

</div>

<div>

## Return Types

The **Set-CsVoiceRoute** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route object.

</div>

<div>

## See Also


[New-CsVoiceRoute](new-csvoiceroute.md)  
[Remove-CsVoiceRoute](remove-csvoiceroute.md)  
[Get-CsVoiceRoute](get-csvoiceroute.md)  
[Test-CsVoiceRoute](test-csvoiceroute.md)  
[Get-CsPstnUsage](get-cspstnusage.md)  
[Get-CsService](get-csservice.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

