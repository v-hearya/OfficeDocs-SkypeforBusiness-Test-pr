---
title: Get-CsNetworkRegionLink
TOCTitle: Get-CsNetworkRegionLink
ms:assetid: dc5cb988-13e2-4af4-8b36-0aaa58ebf1c5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398972(v=OCS.15)
ms:contentKeyID: 48185593
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsNetworkRegionLink

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Retrieves one or more links between network regions configured for call admission control (CAC). This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsNetworkRegionLink [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsNetworkRegionLink [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 retrieves all network region links defined within a Lync Server deployment.

    Get-CsNetworkRegionLink

</div>

<div>

## EXAMPLE 2

Example 2 retrieves information about (at most) one network region link, the link with the Identity NA\_EMEA.

    Get-CsNetworkRegionLink -Identity NA_EMEA

</div>

<div>

## EXAMPLE 3

In this example we use the Filter parameter to retrieve all network region links with the string EMEA in the name (Identity) of the link. Notice the \* characters, one before the string EMEA and one after. This means any character or characters can precede or follow the string; the string EMEA simply must be included in the Identity somewhere. This will retrieve links with names such as NA\_EMEA, EMEA\_APAC, and EMEA2\_SA.

    Get-CsNetworkRegionLink -Filter *EMEA*

</div>

<div>

## EXAMPLE 4

This example retrieves all network region links that include EMEA as one of the two regions being linked. The example begins by calling the **Get-CsNetworkRegionLink** cmdlet with no parameters, which will retrieve all region links. This collection of links is then piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet looks through each member of the collection one-by-one, checking the values of the NetworkRegionID1 and NetworkRegionID2 properties. If either of these properties is equal to EMEA--in other words if either NetworkRegionID1 is equal to (-eq) EMEA or (-or) NetworkRegionID2 is equal to (-eq) EMEA--then we want to keep that item in the collection and display it.

    Get-CsNetworkRegionLink | Where-Object {$_.NetworkRegionID1 -eq "EMEA" -or $_.NetworkRegionID2 -eq "EMEA"}

</div>

</div>

<div>

## Detailed Description

Regions within a network are linked through physical WAN connectivity. This cmdlet retrieves one or more region links that are defined within the network configuration settings for a Lync Server deployment.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsNetworkRegionLink** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsNetworkRegionLink"}

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
<td><p>Accepts a wildcard string that is used to retrieve network links based on matching the value of the Identity to the wildcard string.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>The unique identifier of the network region link you want to retrieve. Network region links are created only at the global scope, so this identifier does not need to specify a scope. Instead, it contains a string that is a unique name that identifies that link. (Note that this value is the same as the NetworkRegionLinkID.)</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the network region link information from the local replica of the Central Management store, rather than the Central Management store itself.</p></td>
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

Retrieves one or more objects of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType.

</div>

<div>

## See Also


[New-CsNetworkRegionLink](new-csnetworkregionlink.md)  
[Remove-CsNetworkRegionLink](remove-csnetworkregionlink.md)  
[Set-CsNetworkRegionLink](set-csnetworkregionlink.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

