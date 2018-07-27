---
title: Remove-CsNetworkInterSitePolicy
TOCTitle: Remove-CsNetworkInterSitePolicy
ms:assetid: daf1afc8-cce4-4192-8ba4-05d26817198e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398963(v=OCS.15)
ms:contentKeyID: 48185557
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsNetworkInterSitePolicy

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Removes a network inter-site policy that defines bandwidth limitations between sites that are directly linked within a call admission control (CAC) configuration. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsNetworkInterSitePolicy -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example removes the network site policy with the Identity Reno\_Portland.

    Remove-CsNetworkInterSitePolicy -Identity Reno_Portland

</div>

<div>

## EXAMPLE 2

In Example 2, we remove all network site policies defined within the CAC configuration. We begin by calling the **Get-CsNetworkInterSitePolicy** cmdlet to retrieve a collection of all network site policies. That collection is then piped to the **Remove-CsNetworkInterSitePolicy** cmdlet, which removes each item in the collection.

    Get-CsNetworkInterSitePolicy | Remove-CsNetworkInterSitePolicy

</div>

</div>

<div>

## Detailed Description

When network sites share a direct link, bandwidth limitations for audio and video connections can be defined between those two sites. This cmdlet removes a network site policy that associates a bandwidth limitation policy with two directly connected sites.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsNetworkInterSitePolicy** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsNetworkInterSitePolicy"}

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
<td><p>The unique identifier of the network site policy you want to remove. Network site policies are created only at the global scope, so this identifier does not need to specify a scope. Instead, it contains a string that is a unique name that identifies that site policy.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkSitePolicyType object. Accepts pipelined input of network inter-site policy objects.

</div>

<div>

## Return Types

This cmdlet does not return a value. It removes an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkSitePolicyType.

</div>

<div>

## See Also


[New-CsNetworkInterSitePolicy](new-csnetworkintersitepolicy.md)  
[Set-CsNetworkInterSitePolicy](set-csnetworkintersitepolicy.md)  
[Get-CsNetworkInterSitePolicy](get-csnetworkintersitepolicy.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

