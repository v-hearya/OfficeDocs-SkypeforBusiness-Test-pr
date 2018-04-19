---
title: Remove-CsNetworkBandwidthPolicyProfile
TOCTitle: Remove-CsNetworkBandwidthPolicyProfile
ms:assetid: 7b1f3c8d-486c-4a7e-aa40-57893f249f66
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398609(v=OCS.15)
ms:contentKeyID: 48184596
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsNetworkBandwidthPolicyProfile

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Removes a network bandwidth policy profile. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsNetworkBandwidthPolicyProfile -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example removes the bandwidth policy profile with the Identity LowBWProfile. Because identities must be unique this will remove, at most, one profile.

    Remove-CsNetworkBandwidthPolicyProfile -Identity LowBWProfile

</div>

<div>

## EXAMPLE 2

Example 2 removes all references to the bandwidth policy profile with the Identity LowBWProfile from all sites to which it has been assigned, and then removes that profile. The first line of this example begins with a call to the **Get-CsNetworkSite** cmdlet to retrieve all sites configured for call admission control (CAC). This collection of sites is then piped to the **Where-Object** cmdlet, which looks for only those sites with a BWPolicyProfileID that is equal to (-eq) LowBWProfile. This narrowed-down collection, containing only sites with a BWPolicyProfileID value of LowBWProfile, is piped to the **Set-CSNetworkSite** cmdlet, which modifies each of these sites to change the BWPolicyProfileID to Null ($null). What we’ve just done is to find all sites with a BWPolicyProfileID of LowBWProfile and set that value to Null. At this point there are no sites using the LowBWProfile profile. We now call the **Remove-CsNetworkBandwidthPolicyProfile** cmdlet on the profile LowBWProfile to remove the profile, knowing that the profile is not in use by any sites.

To ensure that the profile is not in use anywhere in the network configuration, perform the same steps in Line 1 against inter-site policies and network region links.

    Get-CsNetworkSite | Where-Object {$_.BWPolicyProfileID -eq "LowBWProfile"} | Set-CsNetworkSite -BWPolicyProfileID $null
    Remove-CsNetworkBandwidthPolicyProfile -Identity LowBWProfile

</div>

</div>

<div>

## Detailed Description

As part of call admission control (CAC), a bandwidth policy is used to define bandwidth limitations for certain modalities. (In Lync Server, only audio and video modalities can be assigned bandwidth limitations.) This cmdlet removes a container profile for these policies.

IMPORTANT: If a profile has been assigned to a site (by using the **New-CsNetworkSite** cmdlet or the **Set-CsNetworkSite** cmdlet), to an inter-site policy (by using the **New-CsNetworkInterSitePolicy** cmdlet or the **Set-CsNetworkInterSitePolicy** cmdlet), or to a network region link (by using the **New-CsNetworkRegionLink** cmdlet or the **Set-CsNetworkRegionLink** cmdlet) it cannot be removed. You will receive an error if you try to remove the profile by calling the **Remove-CsNetworkBandwidthPolicyProfile** cmdlet. You must first remove the profile from all sites, inter-site policies, and network region links, and then you can remove the profile.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsNetworkBandwidthPolicyProfile** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsNetworkBandwidthPolicyProfile"}

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
<td><p>A string value that uniquely identifies the bandwidth policy profile you want to remove. Specifying an Identity will remove, at most, one profile.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyProfileType object. Accepts pipelined input of network bandwidth policy profile objects.

</div>

<div>

## Return Types

This cmdlet does not return a value. It removes an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyProfileType.

</div>

<div>

## See Also


[New-CsNetworkBandwidthPolicyProfile](new-csnetworkbandwidthpolicyprofile.md)  
[Set-CsNetworkBandwidthPolicyProfile](set-csnetworkbandwidthpolicyprofile.md)  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

