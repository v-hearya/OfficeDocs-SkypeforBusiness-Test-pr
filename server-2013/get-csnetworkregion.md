---
title: Get-CsNetworkRegion
TOCTitle: Get-CsNetworkRegion
ms:assetid: 5c9eef10-16c1-45f7-ae7b-2bee0965b421
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398406(v=OCS.15)
ms:contentKeyID: 48184281
ms.date: 07/07/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsNetworkRegion

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Retrieves one or more network regions. Network regions represent network hubs or backbones in an enterprise network. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsNetworkRegion [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsNetworkRegion [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 retrieves all network regions defined for the organization.

    Get-CsNetworkRegion

</div>

<div>

## EXAMPLE 2

Example 2 retrieves the network regions with the Identity NorthAmerica. Because identities are unique, this command retrieves at most one network region.

    Get-CsNetworkRegion -Identity NorthAmerica

</div>

<div>

## EXAMPLE 3

This example retrieves all network regions with identities that end with the string "America." This would retrieve regions with identities such as NorthAmerica, SouthAmerica, and CentralAmerica.

    Get-CsNetworkRegion | Where-Object {$_.CentralSite -eq "site:Redmond"}

</div>

<div>

## EXAMPLE 4

This example retrieves all network regions associated with the central site Redmond. The command begins by calling the **Get-CsNetworkRegion** cmdlet, with no parameters, to retrieve a collection of all network regions defined for the Lync Server deployment. This collection is then piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet filters this collection to return only those items (network regions) where the CentralSite value is equal to (-eq) site:Redmond.

    Get-CsNetworkRegion | Where-Object {$_.CentralSite -eq "site:Redmond"}

</div>

</div>

<div>

## Detailed Description

A network region interconnects various parts of a network across multiple geographic areas. Every network region must be associated with a central site. Use this cmdlet to retrieve information about one or more network regions, including the associated central site and settings that determine whether alternate paths are allowed for audio and video connections, and that associate the sites within the region with a media bypass configuration.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsNetworkRegion** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsNetworkRegion"}

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
<td><p><em>Filter</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>This parameter allows you to perform a wildcard search on the Identity of all network regions configured for the organization. Use the wildcard character to filter on any part of the Identity.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>The unique identifier of the network region you want to retrieve. The Identity will be in the form of a string that uniquely identifies that region. (Note that the Identity is the same as the NetworkRegionID.)</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the network region information from the local replica of the Central Management store, rather than the Central Management store itself.</p></td>
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

Returns one or more objects of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionType.

</div>

<div>

## See Also


[New-CsNetworkRegion](new-csnetworkregion.md)  
[Remove-CsNetworkRegion](remove-csnetworkregion.md)  
[Set-CsNetworkRegion](set-csnetworkregion.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

