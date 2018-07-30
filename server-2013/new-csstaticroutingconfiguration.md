---
title: New-CsStaticRoutingConfiguration
TOCTitle: New-CsStaticRoutingConfiguration
ms:assetid: 30d1736f-990f-46e8-931f-9247cd988244
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425811(v=OCS.15)
ms:contentKeyID: 48183767
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsStaticRoutingConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Creates a new collection of static routing configuration settings. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    New-CsStaticRoutingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Route <PSListModifier>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 creates a new static routing configuration collection with the Identity service:Registrar:atl-cs-001.litwareinc.com. Because the Route parameter is not included in the command, the new collection will not have any static routes assigned to it.

    New-CsStaticRoutingConfiguration -Identity "service:Registrar:atl-cs-001.litwareinc.com" 

</div>

<div>

## EXAMPLE 2

The commands shown in Example 2 create a new SIP proxy route that uses TCP as its transport; this new route is then added to a new static routing configuration collection. To do this, the first command in the example uses the **New-CsStaticRoute** cmdlet to create a new route that points to the next hop server with the IP address 192.168.1.100. This new route (stored in a variable named $x) also uses port 8025 and the MatchUri "\*.litwareinc.com".

After that, the **New-CsStaticRoutingConfiguration** cmdlet is called to create a new collection (with the Identity service:Registrar:atl-cs-001.litwareinc.com), assigning the route stored in the variable $x to the Route property of the new collection.

    $x = New-CsStaticRoute -TCPRoute -Destination "192.168.0.100" -Port 8025 -MatchUri "*.litwareinc.com"
    
    New-CsStaticRoutingConfiguration -Identity "service:Registrar:atl-cs-001.litwareinc.com" -Route $x

</div>

</div>

<div>

## Detailed Description

When you send a SIP message to someone that message might need to traverse multiple subnets and networks before it is delivered; the path traveled by the message is often referred to as a route. In networking, there are two types of routes: dynamic and static. With dynamic routing, servers use algorithms to determine the next location (the next hop) where a message should be forwarded. With static routing, message paths are predetermined by system administrators. When a message is received by a server, the server checks the message address and then forwards the message to the next hop server that has been preconfigured by an administrator. If configured correctly, static routes help ensure timely, and accurate, delivery of messages, and with minimal overheard placed on servers. The downside to static routes is that messages are not dynamically rerouted in the event of a network failure.

When you install Lync Server, a global collection of static routes is automatically created for you. In addition to that, you can use the **New-CsStaticRoutingConfiguration** cmdlet to create additional collections and the site scope or the service scope (for the Registrar service only).

Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsStaticRoutingConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsStaticRoutingConfiguration"}

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
<td><p>Unique identifier for the new static routing collection to be created. New collections can only be created at the service scope, and can only be assigned to the Registrar service. Because of that, the Identity for a new collection must look similar to this: -Identity &quot;service:Registrar:atl-cs-001.litwareinc.com&quot;.</p></td>
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
<td><p><em>InMemory</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet’s matching Set- cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><em>Route</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>Individual static routes maintained within the collection. Routes to be added to a collection must either by copied from another collection or created using the <strong>New-CsStaticRoute</strong> cmdlet. For details, see the Examples section in this topic.</p></td>
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

None. The **New-CsStaticRoutingConfiguration** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **New-CsStaticRoutingConfiguration** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.RoutingSettings object.

</div>

<div>

## See Also


[Get-CsStaticRoutingConfiguration](get-csstaticroutingconfiguration.md)  
[New-CsStaticRoute](new-csstaticroute.md)  
[Remove-CsStaticRoutingConfiguration](remove-csstaticroutingconfiguration.md)  
[Set-CsStaticRoutingConfiguration](set-csstaticroutingconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

