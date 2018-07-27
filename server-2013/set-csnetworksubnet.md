---
title: Set-CsNetworkSubnet
TOCTitle: Set-CsNetworkSubnet
ms:assetid: 9e85cdbb-b5fb-48d6-8f95-6e7cba9d9597
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412739(v=OCS.15)
ms:contentKeyID: 48184923
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsNetworkSubnet

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-25_

Modifies an existing network subnet. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsNetworkSubnet [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsNetworkSubnet [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-MaskBits <Int32>] [-NetworkSiteID <String>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example modifies the subnet with the Identity (the Subnet ID) 172.11.15.0. The subnet is modified with a new MaskBits value (25) and a new NetworkSiteID (Chicago).

    Set-CsNetworkSubnet -Identity 172.11.15.0 -MaskBits 25 -NetworkSiteID Chicago

</div>

<div>

## EXAMPLE 2

Example 2 moves all subnets on the Vancouver site to the Chicago site. To do this, we begin by calling the **Get-CsNetworkSubnet** cmdlet. This will retrieve a collection of all subnets defined within the Lync Server deployment. This collection of subnets is then piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet takes that collection and narrows it down to only those subnets with a NetworkSiteID equal to (-eq) Vancouver. Now that the collection consists only of subnets associated with the Vancouver site, we pipe the collection to the **Set-CsNetworkSubnet** cmdlet. We supply one parameter to the **Set-CsNetworkSubnet** cmdlet: NetworkSiteID. By passing the parameter a value of Chicago, we’re instructing the **Set-CsNetworkSubnet** cmdlet to change the network site ID of every member of the collection to Chicago.

    Get-CsNetworkSubnet | Where-Object {$_.NetworkSiteID -eq "Vancouver"} | Set-CsNetworkSubnet -NetworkSiteID Chicago

</div>

</div>

<div>

## Detailed Description

Each subnet must be associated with a network site for the purposes of determining the geographic location of the host belonging to this subnet. Use this cmdlet to modify the associated network site, change the description of the subnet, or modify the mask bits for the subnet.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsNetworkSubnet** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsNetworkSubnet"}

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
<td><p><em>Description</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>A description of the subnet being modified.</p></td>
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
<td><p>XdsGlobalRelativeIdentity</p></td>
<td><p>The unique subnet ID of the subnet you want to modify. This value will be either an IP address (such as 174.11.12.0) or a URL beginning with http: or https:.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>Optional</p></td>
<td><p>SubnetType</p></td>
<td><p>A reference to the network subnet object that you want to modify. This object must be of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.SubnetType, which can be retrieved by calling the <strong>Get-CsNetworkSubnet</strong> cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>MaskBits</em></p></td>
<td><p>Optional</p></td>
<td><p>Int32</p></td>
<td><p>The bitmask to be applied to the subnet.</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkSiteID</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The site ID of the network site to which this subnet is to be applied. You can retrieve site IDs for your deployment by calling the <strong>Get-CsNetworkSite</strong> cmdlet.</p></td>
</tr>
<tr class="even">
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

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.SubnetType object. Accepts pipelined input of network subnet objects.

</div>

<div>

## Return Types

This cmdlet does not return a value. It modifies an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.SubnetType.

</div>

<div>

## See Also


[New-CsNetworkSubnet](new-csnetworksubnet.md)  
[Remove-CsNetworkSubnet](remove-csnetworksubnet.md)  
[Get-CsNetworkSubnet](get-csnetworksubnet.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

