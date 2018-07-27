---
title: Get-CsNetworkBandwidthPolicyProfile
TOCTitle: Get-CsNetworkBandwidthPolicyProfile
ms:assetid: 31784852-0cf4-4114-bf92-5eef6f346c47
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425815(v=OCS.15)
ms:contentKeyID: 48183771
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsNetworkBandwidthPolicyProfile

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Retrieves one or more network bandwidth policy profiles. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsNetworkBandwidthPolicyProfile [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsNetworkBandwidthPolicyProfile [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Calling the **Get-CsNetworkBandwidthPolicyProfile** cmdlet without any parameters will retrieve all bandwidth policy profiles defined within the Lync Server deployment.

    Get-CsNetworkBandwidthPolicyProfile

</div>

<div>

## EXAMPLE 2

This example retrieves the bandwidth policy profile with the Identity LowBWProfile. Because identities must be unique this will return, at most, one profile.

    Get-CsNetworkBandwidthPolicyProfile -Identity LowBWProfile

</div>

<div>

## EXAMPLE 3

In this example we use the Filter parameter to specify one or more profiles to retrieve based on a wildcard string. We’ve used the string \*50MB\*, which indicates that we want to retrieve all the bandwidth policy profiles with Identity values that contain the string 50MB anywhere within the value. For example, this would retrieve profiles with identities such as “BW profile for 50MB links”, “50MB audio limit”, and “video limits of 50MB”.

    Get-CsNetworkBandwidthPolicyProfile -Filter *50MB*

</div>

</div>

<div>

## Detailed Description

As part of call admission control (CAC), a bandwidth policy is used to define bandwidth limitations for certain modalities. (In Lync Server, only audio and video modalities can be assigned bandwidth limitations.) This cmdlet retrieves one or more container profiles for these policies.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsNetworkBandwidthPolicyProfile** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsNetworkBandwidthPolicyProfile"}

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
<td><p>A string containing wildcards that is used to retrieve bandwidth policy profiles that have Identity values that match the wildcard pattern.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>A string value that uniquely identifies the bandwidth policy profile you want to retrieve. Specifying an Identity will retrieve, at most, one profile.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the network bandwidth policy profile from the local replica of the Central Management store, rather than the Central Management store itself.</p></td>
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

Returns an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyProfileType.

</div>

<div>

## See Also


[New-CsNetworkBandwidthPolicyProfile](new-csnetworkbandwidthpolicyprofile.md)  
[Remove-CsNetworkBandwidthPolicyProfile](remove-csnetworkbandwidthpolicyprofile.md)  
[Set-CsNetworkBandwidthPolicyProfile](set-csnetworkbandwidthpolicyprofile.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

