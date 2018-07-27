---
title: Get-CsNetworkConfiguration
TOCTitle: Get-CsNetworkConfiguration
ms:assetid: 08bc8eca-b244-4d5e-b089-1cc95605ba14
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398140(v=OCS.15)
ms:contentKeyID: 48183339
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsNetworkConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Retrieves global settings for call admission control (CAC), Enhanced 9-1-1 (E9-1-1), and media bypass. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsNetworkConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsNetworkConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example retrieves the network configuration settings. These settings are defined only at the global scope, so only one item will be returned.

    Get-CsNetworkConfiguration

</div>

<div>

## EXAMPLE 2

Only one set of media bypass settings exists, which is applied globally. These settings are stored as part of the overall network configuration. This command first retrieves that configuration by calling the **Get-CsNetworkConfiguration** cmdlet, and then retrieves the MediaBypassSettings property of the configuration.

    (Get-CsNetworkConfiguration).MediaBypassSettings

</div>

</div>

<div>

## Detailed Description

The network configuration object contains all the global settings for media bypass and for an entire CAC configuration within a Lync Server deployment, including whether or not that configuration has been enabled. You can use this cmdlet to retrieve these configurations and settings. However, other than EnableBandwidthPolicyCheck and MediaBypassSettings, it’s recommended that you use cmdlets specific to the object type for retrieving the CAC configuration settings. For example, to retrieve the network regions, it will usually be easier to call the **Get-CsNetworkRegion** cmdlet than to call the **Get-CsNetworkConfiguration** cmdlet and then retrieve the NetworkRegions property of that configuration.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsNetworkConfiguration** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsNetworkConfiguration"}

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
<td><p>Because there will only ever be one network configuration, you do not need this parameter for this cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>This will always be Global.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the network configuration from the local replica of the Central Management store, rather than the Central Management store itself.</p></td>
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

The **Get-CsNetworkConfiguration** cmdlet returns an instance of the Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkConfigurationSettings object.

</div>

<div>

## See Also


[Remove-CsNetworkConfiguration](remove-csnetworkconfiguration.md)  
[Set-CsNetworkConfiguration](set-csnetworkconfiguration.md)  
[Get-CsNetworkSite](get-csnetworksite.md)  
[Get-CsNetworkRegionLink](get-csnetworkregionlink.md)  
[Get-CsNetworkInterSitePolicy](get-csnetworkintersitepolicy.md)  
[Get-CsNetworkInterRegionRoute](get-csnetworkinterregionroute.md)  
[Get-CsNetworkRegion](get-csnetworkregion.md)  
[Get-CsNetworkSubnet](get-csnetworksubnet.md)  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

