---
title: Set-CsNetworkSite
TOCTitle: Set-CsNetworkSite
ms:assetid: 221a099c-72c4-4eb0-8812-6b2b7639a9ee
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398295(v=OCS.15)
ms:contentKeyID: 48183606
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsNetworkSite

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-25_

Modifies an existing network site that has been defined for call admission control (CAC) or Enhanced 9-1-1 (E9-1-1). This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsNetworkSite [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsNetworkSite [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-BWPolicyProfileID <String>] [-BypassID <String>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-EnableLocationBasedRouting <$true | $false>] [-Force <SwitchParameter>] [-LocationPolicy <String>] [-NetworkRegionID <String>] [-VoiceRoutingPolicy <String>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

In this example the network site named Vancouver is modified. The name of the site being modified is specified as the value for the Identity parameter. The Vancouver site is being moved to a new region, which requires that the NetworkRegionID parameter be changed, in this case to the region named Canada. Because a NetworkRegionID has been supplied but no value has been specified for BypassID, a BypassID value will be automatically generated. Any previously-existing bypass ID will be overwritten.

    Set-CsNetworkSite -Identity Vancouver -NetworkRegionID Canada

</div>

<div>

## EXAMPLE 2

Example 2 simply modifies the bandwidth policy profile associated with the Vancouver site. The site name is specified as the value for the Identity parameter. Then we specify a value for the BWPolicyProfileID parameter: LowBWLimits. The policies associated with that profile will be used for this site.

    Set-CsNetworkSite -Identity Vancouver - BWPolicyProfileID LowBWLimits

</div>

</div>

<div>

## Detailed Description

Network sites are the offices or locations configured within each region of a CAC or E9-1-1 deployment. This cmdlet modifies the settings on an existing site. This can include such things as the region with which the site is associated, the description of the site, and the associated bandwidth policy profile.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsNetworkSite** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsNetworkSite"}

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
<td><p>The Identity of the bandwidth policy profile that will define the limitations for this site. You can retrieve a list of available profiles by calling the <strong>Get-CsNetworkBandwidthPolicyProfile</strong> cmdlet.</p>
<p>If you specify a value for this parameter, you must also specify a value for the NetworkRegionID parameter.</p></td>
</tr>
<tr class="even">
<td><p><em>BypassID</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>A globally unique identifier (GUID). This GUID is used to map network sites to media bypass settings within a CAC or E9-1-1 network configuration. (Use this BypassID value in the call to the <strong>New-CsNetworkMediaBypassConfiguration</strong> cmdlet.)</p>
<p>If you specify a value for this parameter you must also specify a value for the NetworkRegionID parameter. If you do not specify a value for this parameter but you do specify a NetworkRegionID, a BypassID will be automatically generated.</p>
<p>If you explicitly specify a value, it must be in the format of a GUID (for example, 3b24a047-dce6-48b2-9f20-9fbff17ed62a). We recommend that you supply a value for NetworkRegionID and allow the BypassID value to be auto-generated. If you manually enter a value, you will receive a confirmation prompt to verify that you don’t want the value to be auto-generated.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>A string that describes the site. This parameter can be used to provide a more descriptive explanation of what the site is for or where it is than can be expressed by the Identity alone.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableLocationBasedRouting</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>When set to True, voice routing will be managed by taking into account the location of both the user placing the call and the user receiving the call. The default value is False.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suppresses any confirmation prompts that would otherwise be displayed before making changes.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>XdsGlobalRelativeIdentity</p></td>
<td><p>The unique identifier of the network site you want to modify. Sites are created only at the global scope, so you do not need to specify a scope. Instead, you need to specify only the network site ID.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Optional</p></td>
<td><p>DisplayNetworkSiteType</p></td>
<td><p>A reference to a network site object (an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.DisplayNetworkSiteType). This object can be retrieved by calling the <strong>Get-CsNetworkSite</strong> cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocationPolicy</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The name of the location policy associated with this site. The location policy assigns specific E9-1-1 settings to the site. To retrieve a list of location policies, call the <strong>Get-CsLocationPolicy</strong> cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkRegionID</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The Identity of the network region that this site is associated with. This parameter must contain a value if you want to provide a BypassID (either through auto-generation or manually), or if the EnableBandwidthPolicyCheck property of the network configuration is True. You can retrieve the network configuration settings by calling the <strong>Get-CsNetworkConfiguration</strong> cmdlet.</p>
<p>If a BypassID exists on this site already and you don’t specify a value for the BypassID parameter, the existing BypassID will be overwritten by an auto-generated BypassID.</p></td>
</tr>
<tr class="odd">
<td><p><em>VoiceRoutingPolicy</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>Per-user voice routing policy to be assigned to the site. For example:</p>
<p>-VoiceRoutingPolicy &quot;RedmondVoiceRouting”</p>
<p>Note that you must specify a per-user policy; global and/or site policies cannot be assigned tio a site using the VoiceRoutingPolicy parameter.</p>
<p>This parameter was introduced in the February, 2013 release of Lync Server 2013.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.DisplayNetworkSiteType object. Accepts pipelined input of network site objects.

</div>

<div>

## Return Types

This cmdlet does not return a value. It modifies an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.DisplayNetworkSiteType.

</div>

<div>

## See Also


[New-CsNetworkSite](new-csnetworksite.md)  
[Remove-CsNetworkSite](remove-csnetworksite.md)  
[Get-CsNetworkSite](get-csnetworksite.md)  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)  
[New-CsNetworkMediaBypassConfiguration](new-csnetworkmediabypassconfiguration.md)  
[Get-CsLocationPolicy](get-cslocationpolicy.md)  
[Get-CsNetworkConfiguration](get-csnetworkconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

