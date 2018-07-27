---
title: Get-CsPoolUpgradeReadinessState
TOCTitle: Get-CsPoolUpgradeReadinessState
ms:assetid: 127c718e-8949-4bcd-b954-5182b8730820
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204689(v=OCS.15)
ms:contentKeyID: 48183464
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsPoolUpgradeReadinessState

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-06-04_

Returns information indicating whether or not your Lync Online Registrar pools are ready to be upgraded. The upgrade readiness state for a pool is based on the upgrade domains that have been configured for that pool. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Get-CsPoolUpgradeReadinessState [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 returns the upgrade readiness state for the local Registrar pool. Note that this command must be executed on a Front End server located within the pool.

    Get-CsPoolUpgradeReadinessState

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The **Get-CsPoolUpgradeReadinessState** cmdlet returns information about the upgrade readiness for a Lync Server 2013 pool. The returned information includes the number of Front End servers assigned to the pool; the number of currently active Front End servers; the name of the upgrade domain; and a True/False value that indicates whether the current state of the pool allows it to be upgraded. Note that this cmdlet must be run locally on a Front End server in the pool being checked. There are no options enabling you to run the **Get-CsPoolUpgradeReadinessState** cmdlet remotely.

**Lync Server Control Panel:** The functions carried out by the **Get-CsPoolUpgradeReadinessState** cmdlet are not available in the Lync Server Control Panel.

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
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
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

<span id="InputTypes"></span>

<div>

## Input Types

None. The **Get-CsPoolUpgradeReadinessState** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **Get-CsPoolUpgradeReadinessState** cmdlet returns an instance of the Microsoft.Rtc.Management.Hadr.PoolUpgradeState object.

</div>

</div>

<span> </span>

</div>

</div>

</div>

