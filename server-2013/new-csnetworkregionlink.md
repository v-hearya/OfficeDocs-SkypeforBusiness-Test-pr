---
title: New-CsNetworkRegionLink
TOCTitle: New-CsNetworkRegionLink
ms:assetid: 61a6a7be-8078-4d59-a78a-2f241f6bf800
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398437(v=OCS.15)
ms:contentKeyID: 48184278
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsNetworkRegionLink

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Creates a link between two regions configured for call admission control (CAC). This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    New-CsNetworkRegionLink -NetworkRegionLinkID <String> <COMMON PARAMETERS>

    New-CsNetworkRegionLink -Identity <XdsGlobalRelativeIdentity> <COMMON PARAMETERS>

    COMMON PARAMETERS: -NetworkRegionID1 <String> -NetworkRegionID2 <String> [-BWPolicyProfileID <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example creates a new network region link named NA\_EMEA to link the regions NorthAmerica and EMEA. The region link name is specified as the value for the Identity parameter. (This will automatically be assigned as the value of the NetworkRegionLinkID.) The two network regions being linked are required parameters for creating the link, in this case the regions named NorthAmerica and EMEA. In this example we’ve also assigned a value to the BWPolicyProfile parameter. This will assign the bandwidth limitations defined in that bandwidth policy profile (LowBWLimits) to connections between these regions. If no BWPolicyProfileID is supplied, there are no bandwidth limitations on connections between these two regions. (There could still be limitations between sites. For details, see the **New-CsNetworkSite** cmdlet help topic.)

    New-CsNetworkRegionLink -Identity NA_EMEA -NetworkRegionID1 NorthAmerica -NetworkRegionID2 EMEA -BWPolicyProfileID LowBWLimits

</div>

</div>

<div>

## Detailed Description

Regions within a network are linked through physical WAN connectivity. This cmdlet defines a link between two regions and sets the bandwidth limitations on audio and video connections between these regions.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsNetworkRegionLink** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsNetworkRegionLink"}

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
<td><p>A unique identifier for the newly created network region link. Network region links are created only at the global scope, so this identifier does not need to specify a scope. Instead, it contains a string that is a unique name that identifies that link.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkRegionID1</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>The Identity (NetworkRegionID) of the region that is linked to the region identified by the NetworkRegionID2 parameter.</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkRegionID2</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>The Identity (NetworkRegionID) of the region that is linked to the region identified by the NetworkRegionID1 parameter.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkRegionLinkID</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>This value is the same as the Identity. You cannot specify both an Identity and a NetworkRegionLinkID; a value entered for one will be automatically used for both.</p></td>
</tr>
<tr class="odd">
<td><p><em>BWPolicyProfileID</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>The Identity of the bandwidth policy profile that will define the bandwidth limitations for this link. You can retrieve a list of available profiles by calling the <strong>Get-CsNetworkBandwidthPolicyProfile</strong> cmdlet.</p></td>
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
<td><p><em>InMemory</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet’s matching Set- cmdlet.</p></td>
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

None.

</div>

<div>

## Return Types

This cmdlet creates an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType.

</div>

<div>

## See Also


[Remove-CsNetworkRegionLink](remove-csnetworkregionlink.md)  
[Set-CsNetworkRegionLink](set-csnetworkregionlink.md)  
[Get-CsNetworkRegionLink](get-csnetworkregionlink.md)  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)  
[New-CsNetworkSite](new-csnetworksite.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

