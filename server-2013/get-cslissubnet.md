---
title: Get-CsLisSubnet
TOCTitle: Get-CsLisSubnet
ms:assetid: 670b50b9-a5ab-4b70-bdb9-bdf3c1b09d0b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398473(v=OCS.15)
ms:contentKeyID: 48184347
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsLisSubnet

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Retrieves one or more subnets from the location configuration database. Each subnet can be associated with a location, in which case this cmdlet will also retrieve the location information of the subnets. This location association is used in an Enhanced 9-1-1 (E9-1-1) Enterprise Voice implementation to notify an emergency services operator of the caller’s location. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsLisSubnet

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 retrieves all Location Information Server (LIS) subnets that have been defined in the Lync Server deployment.

    Get-CsLisSubnet

</div>

<div>

## EXAMPLE 2

This example retrieves all information for the subnet with the IP address 192.0.10.0. The command begins by calling the **Get-CsLisSubnet** cmdlet to retrieve all subnet location associations. This collection of subnet locations is piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet checks the Subnet property of each item in the collection to determine whether the value is equal to (-eq) 192.0.10.0. Because the Subnet ID must be unique, this command will return, at most, one object.

    Get-CsLisSubnet | Where-Object {$_.Subnet -eq "192.0.10.0"}

</div>

</div>

<div>

## Detailed Description

Enhanced 9-1-1 allows an emergency operator to identify the location of a caller without having to ask the caller for that information. In the case where a caller is calling from a Voice over Internet Protocol (VoIP) connection, that information must be extracted based on various connection factors. The VoIP administrator must configure a location map (called a wiremap) that will determine a caller’s location. This cmdlet retrieves information on associations between physical locations and the subnet through which calls are routed.

This cmdlet does not take any parameters (other than the Windows PowerShell common parameters). The cmdlet will retrieve all instances of subnet to location mappings. To narrow down the information retrieved, you must pipe the output from this cmdlet to another Windows PowerShell cmdlet such as the **Where-Object** cmdlet or the **Select-Object** cmdlet.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsLisSubnet** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsLisSubnet"}

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
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>This cmdlet provides only common Windows PowerShell parameters.</p></td>
<td></td>
<td></td>
<td> </td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None.

</div>

<div>

## Return Types

This cmdlet retrieves an object of type System.Management.Automation.PSCustomObject.

</div>

<div>

## See Also


[Remove-CsLisSubnet](remove-cslissubnet.md)  
[Set-CsLisSubnet](set-cslissubnet.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

