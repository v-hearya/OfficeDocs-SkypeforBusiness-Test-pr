---
title: New-CsNetworkBWPolicy
TOCTitle: New-CsNetworkBWPolicy
ms:assetid: bbc91bd1-453c-4ae6-bb77-3b6be9429ed0
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412916(v=OCS.15)
ms:contentKeyID: 48185244
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsNetworkBWPolicy

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Creates a bandwidth policy in memory that can be applied to the bandwidth policy profile. In Lync Server, the policy applies to either audio or video bandwidth. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    New-CsNetworkBWPolicy -BWLimit <UInt32> -BWPolicyModality <Audio | Video> -BWSessionLimit <UInt32>

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example creates a new bandwidth policy and assigns it to the variable $bwp. All parameters for the **New-CsNetworkBWPolicy** cmdlet are required. In this example we specified a total bandwidth limit (BWLimit) of 2000 kbps and a bandwidth session limit (BWSessionLimit) of 300 kbps, and we applied these limits to video sessions (-BWPolicyModality video).

    $bwp = New-CsNetworkBWPolicy -BWLimit 200 -BWSessionLimit 3000 -BWPolicyModality video

</div>

<div>

## EXAMPLE 2

Example 2 expands on Example 1 by assigning the new bandwidth policy to a policy profile. The command in line 1 is identical to Example 1: it creates video bandwidth limitations. Line 2 then calls the **New-CsNetworkBandwidthPolicyProfile** cmdlet to add that policy to a new profile. The new profile receives an Identity of LowBWLimit. Then we use the BWPolicy parameter, giving it the value $bwp, which is the variable containing the new bandwidth policy we just created in Line 1.

    $bwp = New-CsNetworkBWPolicy -BWLimit 200 -BWSessionLimit 3000 -BWPolicyModality video
    New-CsNetworkBandwidthPolicyProfile -Identity LowBWLimit -BWPolicy $bwp

</div>

</div>

<div>

## Detailed Description

This cmdlet creates a new bandwidth policy. A bandwidth policy is used to define bandwidth limitations for certain modalities. (In Lync Server, only audio and video modalities can be assigned bandwidth limitations.) The bandwidth policy is created only in memory, so the output must be assigned to a variable and then passed as a value to the BWPolicy parameter of the **New-CsNetworkBandwidthPolicyProfile** cmdlet or the **Set-CsNetworkBandwidthPolicyProfile** cmdlet. Bandwidth policies are applied to policy profiles, which can store multiple policies for a single profile and are part of the global network configuration for call admission control (CAC).

Note that the recommended method of assigning audio and video policies is to assign them directly to a bandwidth policy profile by calling the **New-CsNetworkBandwidthPolicyProfile** or the **Set-CsNetworkBandwidthPolicyProfile** cmdlet and specifying values for the AudioBWLimit, AudioBWSessionLimit, VideoBWLimit, and VideoBWSessionLimit parameters.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsNetworkBWPolicy** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsNetworkBWPolicy"}

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
<td><p><em>BWLimit</em></p></td>
<td><p>Required</p></td>
<td><p>System.UInt32</p></td>
<td><p>The maximum total bandwidth, in kbps, for all concurrent sessions of the type specified in the BWPolicyModality parameter.</p></td>
</tr>
<tr class="even">
<td><p><em>BWPolicyModality</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyModality</p></td>
<td><p>Determines which type of bandwidth is limited.</p>
<p>Valid values: Audio, Video</p></td>
</tr>
<tr class="odd">
<td><p><em>BWSessionLimit</em></p></td>
<td><p>Required</p></td>
<td><p>System.UInt32</p></td>
<td><p>The maximum bandwidth, in kbps, allowed for a single session of the type specified in the BWPolicyModality parameter.</p></td>
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

Creates an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyType.

</div>

<div>

## See Also


[New-CsNetworkBandwidthPolicyProfile](new-csnetworkbandwidthpolicyprofile.md)  
[Set-CsNetworkBandwidthPolicyProfile](set-csnetworkbandwidthpolicyprofile.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

