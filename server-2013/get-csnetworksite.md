---
title: Get-CsNetworkSite
TOCTitle: Get-CsNetworkSite
ms:assetid: 9627869d-101f-4668-bee2-01fce1d84cbd
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398766(v=OCS.15)
ms:contentKeyID: 48184855
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsNetworkSite

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Retrieves one or more network sites defined for call admission control (CAC) or Enhanced 9-1-1 (E9-1-1). This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsNetworkSite [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsNetworkSite [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Calling the **Get-CsNetworkSite** cmdlet with no parameters will return all network sites configured for CAC or E9-1-1 within the Lync Server deployment.

    Get-CsNetworkSite

</div>

<div>

## EXAMPLE 2

This command retrieves the site with the Identity (and, by definition, the NetworkSiteID) Redmond.

    Get-CsNetworkSite -Identity Redmond

</div>

<div>

## EXAMPLE 3

The command in Example 3 calls the **Get-CsNetworkSite** cmdlet with the Filter parameter. The value of the Filter parameter is NA\*, meaning that this command will retrieve all sites with an Identity beginning with the string NA and followed by any number of characters. This will return sites such as NARedmond, NAVancouver, and NAChicago.

    Get-CsNetworkSite -Filter NA*

</div>

<div>

## EXAMPLE 4

Example 4 uses two cmdlets, the **Get-CsNetworkSite** cmdlet and the **Where-Object** cmdlet, to retrieve all the sites that are part of the NorthAmerica region. The command begins by calling the **Get-CsNetworkSite** cmdlet with no parameters to retrieve all network sites. This collection of sites is then piped to the **Where-Object** cmdlet, which filters the collection, looking for all sites in the collection where the NetworkRegionID property is equal to (-eq) NorthAmerica.

    Get-CsNetworkSite | Where-Object {$_.NetworkRegionID -eq "NorthAmerica"}

</div>

</div>

<div>

## Detailed Description

Network sites are the offices or locations configured within each region of a CAC or E9-1-1 deployment. This cmdlet retrieves the settings for one or more existing sites.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsNetworkSite** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsNetworkSite"}

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
<td><p>A wildcard string that allows you to retrieve multiple sites based on matching the site Identity to the Filter value.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>The unique identifier of the network site you want to retrieve. Sites are created only at the global scope, so you do not need to specify a scope. Instead, you need to specify only the site ID. (Note that this is the same value as the NetworkSiteID for the network site.)</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the network site information from the local replica of the Central Management store, rather than the Central Management store itself.</p></td>
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

Retrieves an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.DisplayNetworkSiteType.

</div>

<div>

## See Also


[New-CsNetworkSite](new-csnetworksite.md)  
[Remove-CsNetworkSite](remove-csnetworksite.md)  
[Set-CsNetworkSite](set-csnetworksite.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

