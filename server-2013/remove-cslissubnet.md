﻿---
title: Remove-CsLisSubnet
TOCTitle: Remove-CsLisSubnet
ms:assetid: f8a87038-cc71-4fec-8496-574da0aa963f
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg413053(v=OCS.15)
ms:contentKeyID: 48185909
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsLisSubnet

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-08-12_

Removes a Location Information Server (LIS) subnet. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsLisSubnet -Subnet <String> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 removes the LIS subnet location entry for the subnet with the IP address 192.10.10.0. The command in this example includes only one (required) parameter: Subnet. The value of the Subnet in this example is an IPv4 address, 192.10.10.0.

If this subnet is associated with a location, that location will not be removed, only the subnet will be removed from the location mapping.

    Remove-CsLisSubnet -Subnet 192.10.10.0

</div>

<div>

## EXAMPLE 2

This example removes all subnets that are associated with the location Bldg30/Room1000. The example begins with a call to the **Get-CsLisSubnet** cmdlet, which returns a collection of all LIS subnets. This collection is piped to the **Where-Object** cmdlet, which finds the items in that collection that have a Location property that is equal to (-eq) the string Bldg30/Room1000. Finally, we pipe this collection of subnets with that Location to the **Remove-CsLisSubnet** cmdlet, which removes everything in that collection.

Note that, as in Example 1, no locations are removed from the location configuration database, only the subnets that reference those locations are removed. You can remove locations by calling the **Remove-CsLisLocation** cmdlet.

    Get-CsLisSubnet | Where-Object {$_.Location -eq "Bldg30/Room1000"} | Remove-CsLisSubnet

</div>

</div>

<div>

## Detailed Description

Enhanced 9-1-1 (E9-1-1) allows an emergency operator to identify the location of a caller without having to ask the caller for that information. In the case where a caller is calling from a Voice over Internet Protocol (VoIP) connection, that information must be extracted based on various connection factors. The VoIP administrator must configure a location map (called a wiremap) that will determine a caller’s location. This cmdlet removes a subnet from the location configuration database. Removing the subnet will not remove the location associated with that subnet. Use the **Remove-CsLisLocation** cmdlet to remove a location.

If you attempt to remove a subnet that does not exist, no action will be taken and you will not receive an error or a warning message.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsLisSubnet** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsLisSubnet"}

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
<td><p><em>Subnet</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>The IP address of the subnet you want to remove. This value will be an IPv4 address (digits separated by periods, such as 192.0.2.0).</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
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

Accepts pipelined input of Location Information Server (LIS) subnet objects.

</div>

<div>

## Return Types

This cmdlet removes an object of type System.Management.Automation.PSCustomObject.

</div>

<div>

## See Also


[Set-CsLisSubnet](set-cslissubnet.md)  
[Get-CsLisSubnet](get-cslissubnet.md)  
[Remove-CsLisLocation](remove-cslislocation.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

