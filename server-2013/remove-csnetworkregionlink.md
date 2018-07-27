---
title: Remove-CsNetworkRegionLink
TOCTitle: Remove-CsNetworkRegionLink
ms:assetid: f26cde90-e789-44a7-a304-695c85e64403
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg413012(v=OCS.15)
ms:contentKeyID: 48185816
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsNetworkRegionLink

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Removes a link between two regions configured for call admission control (CAC). This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsNetworkRegionLink -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This first example removes the network region link with the Identity NA\_EMEA.

    Remove-CsNetworkRegionLink -Identity NA_EMEA

</div>

<div>

## EXAMPLE 2

Example 2 removes all network region links that are using the bandwidth policy profile named HighBWLimits. The first cmdlet called in the example is the **Get-CsNetworkRegionLink** cmdlet (with no parameters), which will retrieve all region links. This collection of links is then piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet looks through each member of the collection one-by-one, checking the value of the BWPolicyProfileID property. If this property is equal to (-eq) HighBWLimits, we pipe that member to the **Remove-CsNetworkRegionLink** cmdlet, which removes the link.

    Get-CsNetworkRegionLink | Where-Object {$_.BWPolicyProfileID -eq "HighBWLimits"} | Remove-CsNetworkRegionLink

</div>

</div>

<div>

## Detailed Description

Regions within a network are linked through physical WAN connectivity. This cmdlet does not impact any physical connections, but it does remove the link from the CAC configuration.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsNetworkRegionLink** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsNetworkRegionLink"}

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
<td><p>The unique identifier of the network region link you want to remove. Network region links are created only at the global scope, so this identifier does not need to specify a scope. Instead, it contains a string that is a unique name that identifies that link.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType object. Accepts pipelined input of network region link objects.

</div>

<div>

## Return Types

This cmdlet does not return a value. It removes an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType.

</div>

<div>

## See Also


[New-CsNetworkRegionLink](new-csnetworkregionlink.md)  
[Set-CsNetworkRegionLink](set-csnetworkregionlink.md)  
[Get-CsNetworkRegionLink](get-csnetworkregionlink.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

