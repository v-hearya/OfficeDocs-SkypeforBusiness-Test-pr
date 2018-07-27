---
title: Remove-CsNetworkInterRegionRoute
TOCTitle: Remove-CsNetworkInterRegionRoute
ms:assetid: 91948c03-2bcb-4e25-b0b6-23827e85bbb3
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398743(v=OCS.15)
ms:contentKeyID: 48184791
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsNetworkInterRegionRoute

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Removes a route that connects network regions within a call admission control (CAC) configuration. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsNetworkInterRegionRoute -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 removes the route with the Identity NA\_APAC\_Route.

    Remove-CsNetworkInterRegionRoute -Identity NA_APAC_Route

</div>

<div>

## EXAMPLE 2

Example 2 removes all region routes that include the NorthAmerica region. The first part of the command is a call to the **Get-CsNetworkInterRegionRoute** cmdlet. This cmdlet, called with no parameters, will retrieve all region routes. Next, this collection of routes is piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet will narrow the collection down to only those routes that have NorthAmerica defined as one of the regions in the route. It does this by checking to see if the route has a NetworkRegionID1 value equal to (-eq) NorthAmerica, or (-or) a NetworkRegionID2 value equal to NorthAmerica. Once the collection contains only the routes that include the NorthAmerica region, we pipe the collection to the **Remove-CsNetworkInterRegionRoute** cmdlet, which removes each of those routes.

    Get-CsNetworkInterRegionRoute | Where-Object {$_.NetworkRegionID1 -eq "NorthAmerica" -or $_.NetworkRegionID2 -eq "NorthAmerica"} | Remove-CsNetworkInterRegionRoute

</div>

</div>

<div>

## Detailed Description

Every region within a CAC configuration must have some way to access every other region. While region links set bandwidth limitations on the connections between regions and also represent the physical links, a route determines which linked path the connection will traverse from one region to another. This cmdlet removes one of these route associations.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsNetworkInterRegionRoute** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsNetworkInterRegionRoute"}

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
<td><p>The unique identifier for the network region route you want to remove. Network region routes are created only at the global scope, so this identifier does not need to specify a scope. Instead, it contains a string that is a unique name that identifies that route.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkRegionRouteType object. Accepts pipelined input of network inter-region route objects.

</div>

<div>

## Return Types

This cmdlet does not return a value. It removes an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkRegionRouteType.

</div>

<div>

## See Also


[New-CsNetworkInterRegionRoute](new-csnetworkinterregionroute.md)  
[Set-CsNetworkInterRegionRoute](set-csnetworkinterregionroute.md)  
[Get-CsNetworkInterRegionRoute](get-csnetworkinterregionroute.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

