---
title: Set-CsNetworkInterRegionRoute
TOCTitle: Set-CsNetworkInterRegionRoute
ms:assetid: 5d9da3c0-56fc-401d-baf3-ed6c0f50f53d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398410(v=OCS.15)
ms:contentKeyID: 48184263
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsNetworkInterRegionRoute

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-25_

Modifies an existing route that connects network regions within a call admission control (CAC) configuration. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsNetworkInterRegionRoute [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsNetworkInterRegionRoute [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-NetworkRegionID1 <String>] [-NetworkRegionID2 <String>] [-NetworkRegionLinkIDs <String>] [-NetworkRegionLinks <PSListModifier>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example modifies the route NA\_APAC\_Route by changing the region links that will be traversed along the route. The NetworkRegionLinkIDs parameter is used with a value of “NA\_SA,SA\_APAC”, which replaces any existing links with the two specified in that string.

    Set-CsNetworkInterRegionRoute -Identity NA_APAC_Route -NetworkRegionLinkIDs "NA_SA,SA_APAC"

</div>

<div>

## EXAMPLE 2

Like Example 1, Example 2 modifies the links within the NA\_APAC\_Route route. However, in this example, instead of replacing all links for that route by using the NetworkRegionLinkIDs parameter, the NetworkRegionLinks parameter is used to add a link to the list of links that already exists on that route. In this case, the link SA\_EMEA is added to the route. The syntax @{add=\<link\>} adds an element to the list of links. You can also use the syntax @{replace=\<link\>} to replace all existing links with those specified by \<link\> (which essentially behaves the same as using NetworkRegionLinkIDs), or the syntax @{remove=\<link\>} to remove a link from the list.

    Set-CsNetworkInterRegionRoute -Identity NA_APAC_Route -NetworkRegionLinks @{add="SA_EMEA"}

</div>

<div>

## EXAMPLE 3

Example 3 modifies the route named NA\_Route5. This example changes one of the regions that comprise this route. The NetworkRegionID2 parameter is used to specify the new region, and then the NetworkRegionLinkIDs parameter is used to create a new list of links to connect the regions of this route.

    Set-CsNetworkInterRegionRoute -Identity NA_Route5 -NetworkRegionID2 SouthAmerica -NetworkRegionLinkIDs "NA_SA,SA_APAC"

</div>

</div>

<div>

## Detailed Description

Every region within a CAC configuration must have some way to access every other region. While region links set bandwidth limitations on the connections between regions and also represent the physical links, a route determines which linked path the connection will traverse from one region to another. This cmdlet modifies that route association.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsNetworkInterRegionRoute** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsNetworkInterRegionRoute"}

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
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suppresses any confirmation prompts that would otherwise be displayed before making changes.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>XdsGlobalRelativeIdentity</p></td>
<td><p>The unique identifier for the network region route you want to modify. Network region routes are created only at the global scope, so this identifier does not need to specify a scope. Instead, it contains a string that is a unique name that identifies that route.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Optional</p></td>
<td><p>InterNetworkRegionRouteType</p></td>
<td><p>An object reference to an existing region route. This object must be of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkRegionRouteType, which can be retrieved by calling the <strong>Get-CsNetworkInterRegionRoute</strong> cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkRegionID1</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The Identity (NetworkRegionID) of one of the two regions connected through this route. The value passed to this parameter must be a different region from the value of the NetworkRegionID2 parameter. (In other words, you can’t route a region to itself.) In addition, the combination of NetworkRegionID1 and NetworkRegionID2 must be unique (for example, you can’t have two routes defined that connect NorthAmerica and EMEA).</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkRegionID2</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The Identity (NetworkRegionID) of one of the two regions connected through this route. The value passed to this parameter must be a different region from the value of the NetworkRegionID1 parameter. (In other words, you can’t route a region to itself.) In addition, the combination of NetworkRegionID1 and NetworkRegionID2 must be unique (for example, you can’t have two routes defined that connect NorthAmerica and EMEA).</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkRegionLinkIDs</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>Allows you to specify all the links for this route as a string of comma-separated values. The values are the identities (NetworkRegionLinkIDs) of the region links. If you enter values for both NetworkRegionLinkIDs and NetworkRegionLinks, NetworkRegionLinkIDs will be ignored. Any links modified using this parameter will replace all existing links in the route.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkRegionLinks</em></p></td>
<td><p>Optional</p></td>
<td><p>PSListModifier</p></td>
<td><p>A list object containing the identities (NetworkRegionLinkIDs) of the region links that apply to this route. For this cmdlet, this parameter differs from the NetworkRegionLinkIDs in that in addition to allowing you to replace all existing links for this route, you can also add or remove individual links.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkRegionRouteType object. Accepts pipelined input of network interregion route objects.

</div>

<div>

## Return Types

This cmdlet does not return a value. It modifies an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkRegionRouteType.

</div>

<div>

## See Also


[New-CsNetworkInterRegionRoute](new-csnetworkinterregionroute.md)  
[Remove-CsNetworkInterRegionRoute](remove-csnetworkinterregionroute.md)  
[Get-CsNetworkInterRegionRoute](get-csnetworkinterregionroute.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

