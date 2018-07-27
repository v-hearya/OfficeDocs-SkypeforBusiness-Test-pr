---
title: Set-CsNetworkConfiguration
TOCTitle: Set-CsNetworkConfiguration
ms:assetid: d54dc154-c092-4be9-8656-f7fec3fbd835
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398927(v=OCS.15)
ms:contentKeyID: 48185524
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsNetworkConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-25_

Modifies the settings for a network configuration. This cmdlet will most often be used to enable or disable call admission control (CAC). This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsNetworkConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsNetworkConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-BWPolicyProfiles <PSListModifier>] [-Confirm [<SwitchParameter>]] [-EnableBandwidthPolicyCheck <$true | $false>] [-Force <SwitchParameter>] [-InterNetworkRegionRoutes <PSListModifier>] [-InterNetworkSitePolicies <PSListModifier>] [-MediaBypassSettings <MediaBypassSettingsType>] [-NetworkRegionLinks <PSListModifier>] [-NetworkRegions <PSListModifier>] [-NetworkSites <PSListModifier>] [-Subnets <PSListModifier>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command in this example will run a validation check against the entire CAC configuration, and then (depending on your responses to any warning prompts that are returned) will enable CAC. If CAC is already enabled (in other words, if the EnableBandwidthPolicyCheck property is True) and you run this command, it will simply run the validation check.

    Set-CsNetworkConfiguration -EnableBandwidthPolicyCheck $True

</div>

</div>

<div>

## Detailed Description

The network configuration object contains all the settings for an entire CAC configuration within a Lync Server deployment, plus media bypass settings. You can use this cmdlet to modify any part of the CAC configuration, and you must use it if you need to change media bypass settings. However, it’s recommended that you use cmdlets specific to the object type when modifying most of the CAC configuration settings. For example, to work with network regions, use the cmdlets ending with the noun CsNetworkRegion rather than manipulating the NetworkRegions parameter of this cmdlet.

The primary use of this cmdlet is to enable (and disable) CAC and apply media bypass settings. After you’ve set up the various components required for your configuration (such as regions, sites, and subnets), you must enable the configuration before it will work. To do this, simply set the EnableBandwidthPolicyCheck parameter to True. Note that running this cmdlet with EnableBandwidthPolicyCheck set to True doesn’t immediately enable CAC. Before it can be enabled, a series of validation checks are made to ensure the setup is configured properly. Any errors or discrepancies in the setup will prompt with warnings that ask if you want to continue to enable CAC even though there is a problem. If you choose to continue (by pressing Enter or Y), the validation will continue and will prompt you again if another issue is discovered.

If you run through the entire validation, choosing to continue at each warning, EnableBandwidthPolicyCheck will be set to True and CAC will be enabled, but until the issues are resolved it probably won’t work as expected. If at any point in the validation you choose to stop validation (by typing N at a warning prompt), validation will end and EnableBandwidthPolicyCheck will remain set to False (the default).

If EnableBandwidthPolicyCheck is already set to True, you can call the **Set-CsNetworkConfiguration** cmdlet and pass a value of True to the parameter EnableBandwidthPolicyCheck to run the validation without modifying any settings. In addition, when EnableBandwidthPolicyCheck is True, any changes you attempt to make by calling the **Set-CsNetworkConfiguration** cmdlet will again cause the validation check to run.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsNetworkConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsNetworkConfiguration"}

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
<td><p><em>BWPolicyProfiles</em></p></td>
<td><p>Optional</p></td>
<td><p>PSListModifier</p></td>
<td><p>A collection of all the bandwidth policy profiles that can be assigned to sites, inter-site policies, and network region links. Each bandwidth policy profile contains bandwidth limitations (overall limitations and session limitations) for audio and/or video connections. A full list of bandwidth policy profiles can be retrieved by calling the <strong>Get-CsNetworkBandwidthPolicyProfile</strong> cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableBandwidthPolicyCheck</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>Setting this parameter to True will run a validation check against the entire CAC configuration. If all validation checks pass, or if you choose to ignore all warnings, CAC will be enabled. If a validation check does not pass, you can choose to stop the validation and the value of EnableBandwidthPolicyCheck will not change. You must have region routes defined between each pair of network regions before you running the validation check.</p>
<p>Setting this value to False will disable CAC.</p>
<p>Default: False</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>This parameter does not take a value. If you include this parameter, any changes made to the configuration, including enabling the configuration, will take place with no warnings or validation checks.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>XdsIdentity</p></td>
<td><p>This value will always be Global.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Optional</p></td>
<td><p>NetworkConfigurationSettings</p></td>
<td><p>A reference to a network configuration object. This object must be of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkConfigurationSettings, which can be retrieved by calling the <strong>Get-CsNetworkConfiguration</strong> cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><em>InterNetworkRegionRoutes</em></p></td>
<td><p>Optional</p></td>
<td><p>PSListModifier</p></td>
<td><p>A collection of all the network region routes defined within the CAC configuration. You can retrieve all the members of this collection by calling the <strong>Get-CsNetworkInterRegionRoute</strong> cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>InterNetworkSitePolicies</em></p></td>
<td><p>Optional</p></td>
<td><p>PSListModifier</p></td>
<td><p>A collection of network inter-site policies defined within the CAC configuration. You can retrieve all the members of this collection by calling the <strong>Get-CsNetworkInterSitePolicy</strong> cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><em>MediaBypassSettings</em></p></td>
<td><p>Optional</p></td>
<td><p>MediaBypassSettingsType</p></td>
<td><p>A reference to an object that defines the global media bypass settings for the CAC configuration. Setting this value will overwrite all existing media bypass settings. You obtain this object reference by calling the <strong>New-CsNetworkMediaBypassConfiguration</strong> cmdlet and assigning the new configuration settings to a variable. Pass this variable to the MediaBypassSettings parameter to change the global media bypass settings.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkRegionLinks</em></p></td>
<td><p>Optional</p></td>
<td><p>PSListModifier</p></td>
<td><p>A collection of network region links defined within the CAC configuration. Each network region link defines a connection that exists between two regions and any bandwidth limitations that should be applied to connections between those regions. You can retrieve all the members of this collection by calling the <strong>Get-CsNetworkRegionLink</strong> cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkRegions</em></p></td>
<td><p>Optional</p></td>
<td><p>PSListModifier</p></td>
<td><p>A collection of network regions (each of which represents a hub or backbone within the network) defined within the CAC configuration. You can retrieve all the members of this collection by calling the <strong>Get-CsNetworkRegion</strong> cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkSites</em></p></td>
<td><p>Optional</p></td>
<td><p>PSListModifier</p></td>
<td><p>A collection of network sites (each of which represents an office or location within a region) defined within the CAC configuration. You can retrieve all the members of this collection by calling the <strong>Get-CsNetworkSite</strong> cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><em>Subnets</em></p></td>
<td><p>Optional</p></td>
<td><p>PSListModifier</p></td>
<td><p>A collection of network subnets (each of which associates an endpoint with a site) defined within the CAC configuration. You can retrieve all the members of this collection by calling the <strong>Get-CsNetworkSubnet</strong> cmdlet.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkConfigurationSettings object. Accepts pipelined input of a network configuration object.

</div>

<div>

## Return Types

The **Set-CsNetworkConfiguration** cmdlet does not return a value or object. Instead, the cmdlet modifies instances of the Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkConfigurationSettings object.

</div>

<div>

## See Also


[Remove-CsNetworkConfiguration](remove-csnetworkconfiguration.md)  
[Get-CsNetworkConfiguration](get-csnetworkconfiguration.md)  
[Get-CsNetworkSite](get-csnetworksite.md)  
[Get-CsNetworkRegionLink](get-csnetworkregionlink.md)  
[Get-CsNetworkInterSitePolicy](get-csnetworkintersitepolicy.md)  
[Get-CsNetworkInterRegionRoute](get-csnetworkinterregionroute.md)  
[Get-CsNetworkRegion](get-csnetworkregion.md)  
[Get-CsNetworkSubnet](get-csnetworksubnet.md)  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)  
[New-CsNetworkMediaBypassConfiguration](new-csnetworkmediabypassconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

