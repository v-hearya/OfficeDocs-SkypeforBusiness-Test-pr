---
title: New-CsNetworkMediaBypassConfiguration
TOCTitle: New-CsNetworkMediaBypassConfiguration
ms:assetid: 24055ae5-7fc8-4ca5-9e65-ac3a1f17b405
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425718(v=OCS.15)
ms:contentKeyID: 48183635
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsNetworkMediaBypassConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-25_

Creates new global settings for media bypass. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    New-CsNetworkMediaBypassConfiguration [-AlwaysBypass <$true | $false>] [-BypassID <String>] [-Enabled <$true | $false>] [-EnableDefaultBypassID <$true | $false>] [-EnabledForAudioVideoConferences <$true | $false>] [-ExternalBypassMode <Off | ICE | Any>] [-InternalBypassMode <Off | ICE | Any>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The commands in this example enable media bypass and configure it to always attempt bypass. The first line in the example is a call to the **New-CsNetworkMediaBypassConfiguration** cmdlet. We pass two parameters to this cmdlet: AlwaysBypass and Enabled, setting both to True ($true). Setting Enabled to True enables media bypass, while setting AlwaysBypass to True assures that media bypass will be attempted on all calls. (Note that setting these two parameters will automatically generate a value for the BypassID property.) The **New-CsNetworkMediaBypassConfiguration** cmdlet creates the object only in memory, so we assign that object to the variable $a.

The media bypass configuration is stored with the network configuration settings. Therefore, in line 2 of the example, we save the media bypass configuration changes to the network configuration by calling the **Set-CsNetworkConfiguration** cmdlet and passing the media bypass configuration object ($a) we created in line 1 to the MediaBypassSettings parameter.

    $a = New-CsNetworkMediaBypassConfiguration -AlwaysBypass $true -Enabled $true
    Set-CsNetworkConfiguration -MediaBypassSettings $a

</div>

<div>

## EXAMPLE 2

There is no **Set-CsNetworkMediaBypassConfiguration** cmdlet in Lync Server, so in order to modify existing settings you must either create a new configuration (as shown in Example 1) to replace the existing configuration, or you must modify the settings by retrieving the existing settings, modifying them, and then using the **Set-CsNetworkConfiguration** cmdlet to save the changes. This example demonstrates turning off the Always Bypass option by using this latter option.

The first line in the example retrieves the existing media bypass settings. It does this by calling the **Get-CsNetworkConfiguration** cmdlet. The call to this cmdlet is within parentheses to ensure the cmdlet is completed before any other part of the command is run. The **Get-CsNetworkConfiguration** cmdlet retrieves all settings for an entire network configuration. Because we’re interested in only the media bypass settings, we specify the MediaBypassSettings property to retrieve only those settings. We assign those settings to the variable $a.

In line 2 we modify the settings stored in variable $a by assigning the value False ($false) to the AlwaysBypass property. Finally, in line 3 we call the **Set-CsNetworkConfiguration** cmdlet, passing the MediaBypassSettings parameter the variable $a, which saves the change we made to the AlwaysBypass property.

    $a = (Get-CsNetworkConfiguration).MediaBypassSettings
    $a.AlwaysBypass = $false
    Set-CsNetworkConfiguration -MediaBypassSettings $a

</div>

</div>

<div>

## Detailed Description

This cmdlet creates global settings for media bypass of audio connections.

Unlike most New- cmdlets in Lync Server, this cmdlet does not immediately save the new configuration; it creates the settings only in memory. The object created by this cmdlet must be saved to a variable and then assigned to the MediaBypassSettings property of the network configuration. (For more details, see the Examples section in this topic.)

The settings created with this cmdlet can be retrieved only by accessing the MediaBypassSettings property of the global network configuration. To retrieve these settings, run this command: (Get-CsNetworkConfiguration).MediaBypassSettings.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsNetworkMediaBypassConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsNetworkMediaBypassConfiguration"}

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
<td><p><em>AlwaysBypass</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>Setting this parameter to True will attempt media bypass on all calls.</p>
<p>Set this parameter value to True only if call admission control (CAC) is disabled. Set this parameter to True only for deployments where:</p>
<p>- There is no need for bandwidth control.</p>
<p>- There is no need for fine-grained configuration to determine when bypass should happen.</p>
<p>- There is full connectivity between gateways and clients.</p>
<p>If the Enabled parameter is set to True and AlwaysBypass is set to False, bypass logic will use network configuration sites and regions to determine when bypass is possible.</p>
<p>If you set AlwaysBypass to True but do not also set the value of the Enabled parameter to True, you’ll receive a warning message: AlwaysBypass setting is ignored if Enabled is set to false.</p>
<p>Setting AlwaysBypass and Enabled both to True will auto-generate a bypass ID that will be stored in the BypassID property.</p>
<p>Default: False</p></td>
</tr>
<tr class="even">
<td><p><em>BypassID</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The media bypass ID. If the AlwaysBypass parameter is set to True and a value is supplied for this parameter, this BypassID will be associated with all subnets. If AlwaysBypass is False, the BypassID value is associated with all subnets that are not found in network configuration sites and regions.</p>
<p>This ID must be in the format of a GUID (for example, 96f14dea-5170-429a-b92b-f1cb909c4bb6). However, you will typically not have to set or change this parameter. This value is automatically generated when Enabled is set to True and either: 1) AlwaysBypass is set to True, or 2) the EnableDefaultBypassID parameter is set to True.</p></td>
</tr>
<tr class="odd">
<td><p><em>Enabled</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>Set this parameter to True to enable media bypass. At that point bypass decisions will be based on the value of the AlwaysBypass setting as follows:</p>
<p>- If AlwaysBypass is True, attempt bypass for all calls.</p>
<p>- If AlwaysBypass is False, use the network configuration site and region to determine whether bypass is possible.</p>
<p>Default: False</p></td>
</tr>
<tr class="even">
<td><p><em>EnableDefaultBypassID</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>This value applies only when AlwaysBypass is set to False.</p>
<p>Setting this value to True will automatically generate a default bypass ID. This auto-generated value will be stored in the BypassID property.</p>
<p>This parameter is useful when there is a well-connected core with remote sites that have bandwidth constrained links. The administrator will need to define only the subnets associated with the remote sites by way of network configuration sites and regions. Any subnets associated with the core need not be defined and bypass will automatically be attempted between those subnets.</p>
<p>Default: False</p></td>
</tr>
<tr class="odd">
<td><p><em>EnabledForAudioVideoConferences</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>Indicates whether media bypass should be used for audio/video conferences. The default value is False ($False).</p></td>
</tr>
<tr class="even">
<td><p><em>ExternalBypassMode</em></p></td>
<td><p>Optional</p></td>
<td><p>BypassModeEnumType</p></td>
<td><p>Reserved for future use. External media bypass is not supported in Lync Server.</p>
<p>Default: Off</p></td>
</tr>
<tr class="odd">
<td><p><em>InternalBypassMode</em></p></td>
<td><p>Optional</p></td>
<td><p>BypassModeEnumType</p></td>
<td><p>The value of this parameter controls when clients connecting from inside the organization’s network can try to perform media bypass. If Enabled is set to True, this value will automatically be changed to Any. Other values for this parameter are reserved for future use.</p>
<p>Default: Off</p></td>
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

Creates an object reference of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.MediaBypassSettingsType.

</div>

<div>

## See Also


[Get-CsNetworkConfiguration](get-csnetworkconfiguration.md)  
[Set-CsNetworkConfiguration](set-csnetworkconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

