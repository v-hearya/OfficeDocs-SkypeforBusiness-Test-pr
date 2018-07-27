---
title: Remove-CsNetworkSubnet
TOCTitle: Remove-CsNetworkSubnet
ms:assetid: 251ddb5c-4837-4810-b46f-d276f9535653
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425726(v=OCS.15)
ms:contentKeyID: 48183639
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsNetworkSubnet

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Removes an existing network subnet. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsNetworkSubnet -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example removes the subnet with the Identity (the Subnet ID) 172.11.15.0.

    Remove-CsNetworkSubnet -Identity 172.11.15.0

</div>

<div>

## EXAMPLE 2

Example 2 removes all subnets associated with the Vancouver site. To do this, we begin by calling the **Get-CsNetworkSubnet** cmdlet. This will retrieve a collection of all subnets defined within the Lync Server deployment. This collection of subnets is then piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet takes that collection and narrows it down to only those subnets with a NetworkSiteID equal to (-eq) Vancouver. Now that the collection consists only of subnets associated with the Vancouver site, we pipe the collection to the **Remove-CsNetworkSubnet** cmdlet, which removes every item in the collection.

    Get-CsNetworkSubnet | Where-Object {$_.NetworkSiteID -eq "Vancouver"} | Remove-CsNetworkSubnet

</div>

</div>

<div>

## Detailed Description

Each subnet must be associated with a network site for the purposes of determining the geographic location of the host belonging to this subnet. Use this cmdlet to remove a network subnet.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsNetworkSubnet** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsNetworkSubnet"}

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
<td><p>The unique subnet ID of the subnet you want to remove. This value will be an IP address (such as 174.11.12.0).</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.SubnetType object. Accepts pipelined input of network subnet objects.

</div>

<div>

## Return Types

This cmdlet does not return a value. It removes an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.SubnetType.

</div>

<div>

## See Also


[New-CsNetworkSubnet](new-csnetworksubnet.md)  
[Set-CsNetworkSubnet](set-csnetworksubnet.md)  
[Get-CsNetworkSubnet](get-csnetworksubnet.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

