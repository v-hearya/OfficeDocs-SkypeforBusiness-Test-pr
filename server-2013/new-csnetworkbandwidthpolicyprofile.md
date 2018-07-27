---
title: New-CsNetworkBandwidthPolicyProfile
TOCTitle: New-CsNetworkBandwidthPolicyProfile
ms:assetid: 84940891-37a6-45fc-972d-05b95aa71ba9
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398675(v=OCS.15)
ms:contentKeyID: 48184706
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsNetworkBandwidthPolicyProfile

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Creates a new network bandwidth policy profile. This cmdlet can also be used to set the bandwidth policies within the profile. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    New-CsNetworkBandwidthPolicyProfile -Identity <XdsGlobalRelativeIdentity> [-AudioBWLimit <String>] [-AudioBWSessionLimit <String>] [-BWPolicy <PSListModifier>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-VideoBWLimit <String>] [-VideoBWSessionLimit <String>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 creates a new bandwidth policy profile named LowBWLimits. This new profile will have two policies assigned, an audio policy and a video policy (the only two policies possible in Lync Server). The audio policy is added to the profile by using the AudioBWLimit parameter to assign a limit of (in this case) 2000 kbps to overall audio connections, and the AudioBWSessionLimit parameter to assign 200 kbps as the limit for individual audio sessions. The same is done to create video session limits, but using the VideoBWLimit and VideoBWSessionLimit parameters.

    New-CsNetworkBandwidthPolicyProfile -Identity LowBWLimits -AudioBWLimit 2000 -AudioBWSessionLimit 200 -VideoBWLimit 1400 -VideoBWSessionLimit 500

</div>

</div>

<div>

## Detailed Description

As part of call admission control (CAC), a bandwidth policy is used to define bandwidth limitations for certain modalities. (In Lync Server, only audio and video modalities can be assigned bandwidth limitations.) This cmdlet creates a container profile for these policies. You define the individual policies within the container by specifying the audio and video bandwidth limitations when you call this cmdlet.

Bandwidth policy profiles are applied to network sites by calling the **New-CsNetworkSite** cmdlet or the **Set-CsNetworkSite** cmdlet.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsNetworkBandwidthPolicyProfile** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsNetworkBandwidthPolicyProfile"}

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
<td><p>A string value that uniquely identifies the policy. All bandwidth policy profiles are created at the global scope. Therefore the scope is implied and only a unique name needs to be specified when creating a new bandwidth policy profile. Note that this value also populates the BWPolicyProfileID property of the profile.</p></td>
</tr>
<tr class="even">
<td><p><em>AudioBWLimit</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>The maximum amount of bandwidth to allocate for all audio connections. If a single audio session will cause the audio bandwidth limit to be exceeded, that session will not be allowed to start.</p>
<p>Expressed in kbps. For example, a value of 1000 would signify 1000 kbps.</p>
<p>If you supply a value to this parameter, you cannot supply a value to the BWPolicy parameter.</p>
<p>Default: If you supply a value to the AudioBWSessionLimit parameter but not to AudioBWLimit, AudioBWLimit will default to 0.</p></td>
</tr>
<tr class="odd">
<td><p><em>AudioBWSessionLimit</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>The maximum amount of bandwidth to allocate per audio session. Expressed in kbps. Value must be 40 or higher.</p>
<p>If you supply a value to this parameter, you cannot supply a value to the BWPolicy parameter.</p>
<p>Default: If you supply a value to the AudioBWLimit parameter but not to AudioBWSessionLimit, AudioBWSessionLimit will default to 175.</p></td>
</tr>
<tr class="even">
<td><p><em>BWPolicy</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>A list of objects containing bandwidth policy profiles. Each object in the list consists of a bandwidth modality (audio or video), a bandwidth limitation, and a bandwidth session limitation.</p>
<p>If you supply a value to this parameter, you cannot supply a value to the AudioBWLimit, AudioBWSessionLimit, VideoBWLimit, or VideoBWSessionLimit parameter.</p>
<p>Objects in the list can be created by calling the <strong>New-CsNetworkBWPolicy</strong> cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>A description of the bandwidth policy profile. For example, you can use this parameter to clarify the expected use of the profile.</p></td>
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
<td><p><em>VideoBWLimit</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>The maximum amount of bandwidth to allocate for all video connections. If a single video session will cause the video bandwidth limit to be exceeded, that session will not be allowed to start.</p>
<p>Expressed in kbps. For example, a value of 1000 would signify 1000 kbps.</p>
<p>If you supply a value to this parameter, you cannot supply a value to the BWPolicy parameter.</p>
<p>Default: If you supply a value to the VideoBWSessionLimit parameter but not to VideoBWLimit, VideoBWLimit will default to 0.</p></td>
</tr>
<tr class="even">
<td><p><em>VideoBWSessionLimit</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>The maximum amount of bandwidth to allocate per video session. Expressed in kbps. Value must be 100 or higher.</p>
<p>If you supply a value to this parameter, you cannot supply a value to the BWPolicy parameter.</p>
<p>Default: If you supply a value to the VideoBWLimit parameter but not to VideoBWSessionLimit, VideoBWSessionLimit will default to 700.</p></td>
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

Creates an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyProfileType.

</div>

<div>

## See Also


[Remove-CsNetworkBandwidthPolicyProfile](remove-csnetworkbandwidthpolicyprofile.md)  
[Set-CsNetworkBandwidthPolicyProfile](set-csnetworkbandwidthpolicyprofile.md)  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)  
[New-CsNetworkBWPolicy](new-csnetworkbwpolicy.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

