---
title: Get-CsPersistentChatState
TOCTitle: Get-CsPersistentChatState
ms:assetid: 598086c9-a8c7-4b81-84ba-1807f1183024
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204915(v=OCS.15)
ms:contentKeyID: 48184210
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsPersistentChatState

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-07_

Returns the state of one or more Persistent Chat service pools. Persistent Chat pools can be in one of two states: Normal, in which the pool uses its primary databases; or FailedOver, in which the pool uses the backup databases defined in the topology. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Get-CsPersistentChatState [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsPersistentChatState [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 returns the state of all the Persistent Chat servers configured for use in the organization.

    Get-CsPersistentChatState

</div>

<div>

## Example 2

    Get-CsPersistentChatState -Identity "PersistentChatServer:atl-gc-001.litwareinc.com"

</div>

<div>

## Example 3

Example 3 returns state information for all Persistent Chat servers in the domain litwareinc.com. To do this, the Filter parameter is included along with the filter value "\*.litwareinc.com". That filter value causes the **Get-CsPersistentChatState** cmdlet to return information for all the Persistent Chat servers that have an Identity that ends with the string value ".litwareinc.com".

    Get-CsPersistentChatState -Filter "*.litwareinc.com"

</div>

<div>

## Example 4

The command shown in Example 4 returns state information for all the Persistent Chat servers that are currently failed over. To carry out this task, the command first calls the **Get-CsPersistentChatState** cmdlet without any parameters; that returns a collection of all the Persistent Chat servers in the organization. That collection is then piped to the **Where-Object** cmdlet, which picks out only those servers where the PoolState property is equal to (-eq) "FailedOver".

    Get-CsPersistentChatState | Where-Object {$_.PoolState -eq "FailedOver"}

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The **Get-CsPersistentChatState** cmdlet returns the state of one or more Persistent Chat pools. Persistent Chat pools can be in either the Normal state (in which the pool uses its primary databases) or in a FailedOver state, in which the pool uses its backup databases. You can use the [Set-CsPersistentChatState](set-cspersistentchatstate.md) cmdlet to change the state of a Persistent Chat pool; when you change the state of the pool, Lync Server 2013 will automatically change the state of each individual server in the pool.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsPersistentChatState"}

**Lync Server Control Panel:** The functions carried out by the **Get-CsPersistentChatState** cmdlet are not available in the Lync Server Control Panel.

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
<td><p>Enables you to use wildcards when retrieving one or more Persistent Chat states. For example, to return all the Persistent Chat states for the domain litwareinc.com, use this syntax:</p>
<p>-Filter &quot;*.litwareinc.com&quot;</p>
<p>You cannot use both the Filter parameter and the Identity parameter in the same command.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Unique identifier for the Persistent Chat pool. For example:</p>
<p>–Identity &quot;PersistentChatServer:atl-gc-001.litwareinc.com&quot;</p>
<p>If this parameter is omitted then the <strong>Get-CsPersistentChatState</strong> cmdlet returns information for all your Persistent Chat states.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the Persistent Chat state data from the local replica of the Central Management store rather than from the Central Management store itself.</p></td>
</tr>
</tbody>
</table>


</div>

<span id="InputTypes"></span>

<div>

## Input Types

None. The **Get-CsPersistentChatState** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **Get-CsPersistentChatState** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatState object.

</div>

<div>

## See Also


[Set-CsPersistentChatState](set-cspersistentchatstate.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

