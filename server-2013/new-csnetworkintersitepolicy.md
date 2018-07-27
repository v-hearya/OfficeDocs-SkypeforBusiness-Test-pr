---
title: New-CsNetworkInterSitePolicy
TOCTitle: New-CsNetworkInterSitePolicy
ms:assetid: e127153f-a1c3-4a31-8dd3-f08d45eca800
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398994(v=OCS.15)
ms:contentKeyID: 48185532
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsNetworkInterSitePolicy

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-08-12_

Creates a new network inter-site policy that defines bandwidth limitations between sites that are directly linked within a call admission control (CAC) configuration. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    New-CsNetworkInterSitePolicy -InterNetworkSitePolicyID <String> <COMMON PARAMETERS>

    New-CsNetworkInterSitePolicy -Identity <XdsGlobalRelativeIdentity> <COMMON PARAMETERS>

    COMMON PARAMETERS: -NetworkSiteID1 <String> -NetworkSiteID2 <String> [-BWPolicyProfileID <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example creates a new network inter-site policy that limits bandwidth between the connected sites Reno and Portland. The bandwidth limitations for audio and video connections between these sites are limited based on the setting configured for the bandwidth policy profile LowBWLimits.

    New-CsNetworkInterSitePolicy -Identity Reno_Portland -NetworkSiteID1 Reno -NetworkSiteID2 Portland -BWPolicyProfileID LowBWLimits

</div>

</div>

<div>

## Detailed Description

When network sites share a direct link, bandwidth limitations for audio and video connections can be defined between those two sites. This cmdlet creates a network site policy that associates a bandwidth limitation policy with two directly connected sites.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsNetworkInterSitePolicy** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsNetworkInterSitePolicy"}

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
<td><p>A unique identifier for the newly created network inter-site policy. Network inter-site policies are created only at the global scope, so this identifier does not need to specify a scope. Instead, it contains a string that is a unique name that identifies that site policy.</p></td>
</tr>
<tr class="even">
<td><p><em>InterNetworkSitePolicyID</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>This value is the same as the Identity. You cannot specify both an Identity and an InterNetworkSitePolicyID; a value entered for one will be automatically used for both.</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkSiteID1</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>The Identity (NetworkSiteID) of one of the two sites associated with this policy. The combination of NetworkSiteID1 and NetworkSiteID2 must be unique (for example, you can’t have two site policies defined that connect Reno and Portland).</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkSiteID2</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>The Identity (NetworkSiteID) of one of the two sites associated with this policy. The combination of NetworkSiteID1 and NetworkSiteID2 must be unique (for example, you can’t have two site policies defined that connect Reno and Portland).</p></td>
</tr>
<tr class="odd">
<td><p><em>BWPolicyProfileID</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>The Identity of the bandwidth policy profile that will define the limitations for this site policy. You can retrieve a list of available profiles by calling the <strong>Get-CsNetworkBandwidthPolicyProfile</strong> cmdlet.</p></td>
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

Creates an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkSitePolicyType.

</div>

<div>

## See Also


[Remove-CsNetworkInterSitePolicy](remove-csnetworkintersitepolicy.md)  
[Set-CsNetworkInterSitePolicy](set-csnetworkintersitepolicy.md)  
[Get-CsNetworkInterSitePolicy](get-csnetworkintersitepolicy.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

