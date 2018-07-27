---
title: Get-CsNetworkInterSitePolicy
TOCTitle: Get-CsNetworkInterSitePolicy
ms:assetid: a4a64048-f8d7-483a-9565-0c6f3b0937b7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412769(v=OCS.15)
ms:contentKeyID: 48184970
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsNetworkInterSitePolicy

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Retrieves one or more network inter-site policies, which define bandwidth limitations between sites that are directly linked within a call admission control (CAC) configuration. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsNetworkInterSitePolicy [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsNetworkInterSitePolicy [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Calling the **Get-CsNetworkInterSitePolicy** cmdlet with no parameters retrieves all network site policies defined between two directly linked network sites.

    Get-CsNetworkInterSitePolicy

</div>

<div>

## EXAMPLE 2

This example retrieves the network site policy with the Identity Reno\_Portland.

    Get-CsNetworkInterSitePolicy -Identity Reno_Portland

</div>

<div>

## EXAMPLE 3

Example 3 retrieves all network site policies that have the string Reno anywhere within the Identity value. The wildcard characters (\*) within the value passed to the Filter parameter signify “any character or set of characters.” In other words, the string \*Reno\* will match Identity values that begin with any character or characters, followed by the string Reno, followed by any character or characters.

    Get-CsNetworkInterSitePolicy -Filter *Reno*

</div>

<div>

## EXAMPLE 4

This example retrieves all network site policies that do not have a bandwidth policy profile assigned. The command begins by calling the **Get-CsNetworkInterSitePolicy** cmdlet, which, as we saw in Example 1, retrieves a collection of all network site policies. This collection is then piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet narrows the collection down to only those site policies that don’t have a bandwidth policy profile assigned. It does this by comparing to see if the BWPolicyProfileID property of each site policy is equal to (-eq) Null ($null).

    Get-CsNetworkInterSitePolicy | Where-Object {$_.BWPolicyProfileID -eq $null}

</div>

</div>

<div>

## Detailed Description

When network sites share a direct link, bandwidth limitations for audio and video connections can be defined between those two sites. This cmdlet retrieves one or more network site policies that associate bandwidth limitation settings with directly connected sites.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsNetworkInterSitePolicy** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsNetworkInterSitePolicy"}

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
<td><p>A string containing wildcard characters that will search for policies with Identity values matching the wildcard string.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>The unique identifier of the network site policy you want to retrieve. Network site policies are created only at the global scope, so this identifier does not need to specify a scope. Instead, it contains a string that is a unique name that identifies that policy.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the network inter-site policy information from the local replica of the Central Management store, rather than the Central Management store itself.</p></td>
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

Retrieves an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkSitePolicyType.

</div>

<div>

## See Also


[New-CsNetworkInterSitePolicy](new-csnetworkintersitepolicy.md)  
[Remove-CsNetworkInterSitePolicy](remove-csnetworkintersitepolicy.md)  
[Set-CsNetworkInterSitePolicy](set-csnetworkintersitepolicy.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

