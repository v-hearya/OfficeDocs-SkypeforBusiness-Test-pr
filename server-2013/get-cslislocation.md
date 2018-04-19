---
title: Get-CsLisLocation
TOCTitle: Get-CsLisLocation
ms:assetid: aede2266-5af4-4973-9db1-a7b505c62057
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412834(v=OCS.15)
ms:contentKeyID: 48185138
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsLisLocation

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Retrieves one or more locations in the location configuration database for Enhanced 9-1-1 (E9-1-1). This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsLisLocation [-Unreferenced <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Calling the **Get-CsLisLocation** cmdlet with no parameters retrieves all locations defined within the location configuration database.

    Get-CsLisLocation

</div>

<div>

## EXAMPLE 2

The Unreferenced parameter doesn’t accept a value. It’s simply a switch that tells the **Get-CsLisLocation** cmdlet to return only those locations that are not associated with a port, switch, subnet, or wireless access point.

    Get-CsLisLocation -Unreferenced

</div>

<div>

## EXAMPLE 3

In order to retrieve specific LIS locations, you must retrieve all the locations by calling the **Get-CsLisLocation** cmdlet, and then pipe that collection of locations to the **Where-Object** cmdlet to narrow the collection down to the specific locations you’re looking for. Example 3 does just that: it uses the **Get-CsLisLocation** cmdlet and the **Where-Object** cmdlet to retrieve all the locations with a Location property that is equal to the string NorthCampus. (Notice that we used the –ceq comparison operator. This operator does a case-sensitive comparison. That means that in this case only locations with Location values of NorthCampus will be returned; northcampus, Northcampus, etc., will not be returned.)

    Get-CsLisLocation | Where-Object {$_.Location -ceq "NorthCampus"}

</div>

</div>

<div>

## Detailed Description

E9-1-1 enables those who answer emergency calls to determine the caller’s geographic location without having to ask the caller for that information. In Lync Server the location is determined based on mapping the caller’s port, subnet, switch, or wireless access point to a specific location. This cmdlet retrieves one or more of these locations.

This cmdlet differs from the **Get-CsLisCivicAddress** cmdlet in that in addition to retrieving address information, the **Get-CsLisLocation** cmdlet retrieves the name of the location and the company name associated with the location. The **Get-CsLisCivicAddress** cmdlet retrieves only address information.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsLisLocation** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsLisLocation"}

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
<td><p><em>Unreferenced</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Including this parameter will retrieve only the locations that were not associated with a port, subnet, switch, or wireless access point. In other words, including this parameter retrieves all locations that either were created by calling the <strong>Set-CsLisLocation</strong> cmdlet or that were assigned to a Location Information Server (LIS) port, subnet, switch, or wireless access point that no longer exists.</p></td>
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

This cmdlet returns one or more objects of type System.Management.Automation.PSCustomObject.

</div>

<div>

## See Also


[Remove-CsLisLocation](remove-cslislocation.md)  
[Set-CsLisLocation](set-cslislocation.md)  
[Get-CsLisCivicAddress](get-csliscivicaddress.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

