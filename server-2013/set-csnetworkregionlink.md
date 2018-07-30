---
title: Set-CsNetworkRegionLink
TOCTitle: Set-CsNetworkRegionLink
ms:assetid: b3d5d203-2aa7-4a54-93d4-30bcda391d68
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412867(v=OCS.15)
ms:contentKeyID: 48185186
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsNetworkRegionLink

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-25_

Modifies a link between two network regions configured for call admission control (CAC). This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsNetworkRegionLink [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsNetworkRegionLink [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-BWPolicyProfileID <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-NetworkRegionID1 <String>] [-NetworkRegionID2 <String>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example changes the bandwidth policy profile of the network region link named NA\_EMEA to the HighBWLimits profile. The name of the network region link we want to modify is specified as the value for the Identity parameter. Next, we’ve assigned the value HighBWLimits to the BWPolicyProfile parameter. This will assign the bandwidth limitations defined in that bandwidth policy profile (HighBWLimits) to connections between these regions.

    Set-CsNetworkRegionLink -Identity NA_EMEA -BWPolicyProfileID HighBWLimits

</div>

</div>

<div>

## Detailed Description

Regions within a network are linked through physical WAN connectivity. This cmdlet modifies a link between two regions, allowing you to change the regions that are linked as well as the bandwidth limitations on audio and video connections between those regions.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsNetworkRegionLink** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsNetworkRegionLink"}

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
<td><p><em>BWPolicyProfileID</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The Identity of the bandwidth policy profile that will define the limitations for this link. You can retrieve a list of available profiles by calling the <strong>Get-CsNetworkBandwidthPolicyProfile</strong> cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
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
<td><p>The unique identifier for the network region link you want to modify. Network region links are created only at the global scope, so this identifier does not need to specify a scope. Instead, it contains a string that is a unique name that identifies that link.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>Optional</p></td>
<td><p>NetworkRegionLinkType</p></td>
<td><p>An object reference to a network region link. This object must be of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType, which can be retrieved by calling the <strong>Get-CsNetworkRegionLink</strong> cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkRegionID1</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The Identity (NetworkRegionID) of the region that is linked to the region identified by the NetworkRegionID2 property.</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkRegionID2</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The Identity (NetworkRegionID) of the region that is linked to the region identified by the NetworkRegionID1 property.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType object. Accepts pipelined input of network region link objects.

</div>

<div>

## Return Types

This cmdlet does not return a value. It modifies an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType.

</div>

<div>

## See Also


[New-CsNetworkRegionLink](new-csnetworkregionlink.md)  
[Remove-CsNetworkRegionLink](remove-csnetworkregionlink.md)  
[Get-CsNetworkRegionLink](get-csnetworkregionlink.md)  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

