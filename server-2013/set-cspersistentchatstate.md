---
title: Set-CsPersistentChatState
TOCTitle: Set-CsPersistentChatState
ms:assetid: 9b82fe41-214d-4376-b026-bb1434d04118
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205109(v=OCS.15)
ms:contentKeyID: 48184899
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsPersistentChatState

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-07_

Modifies the state of a Persistent Chat service pool. Persistent Chat pools can be in one of two states: Normal, in which the pool uses its primary databases; or FailedOver, in which the pool uses the backup databases defined in the topology. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Set-CsPersistentChatState [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsPersistentChatState [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-PoolState <FailedOver | Normal>] [-WhatIf [<SwitchParameter>]]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 sets the pool state for the Persistent Chat server atl-gc-001.litwareinc.com to FailedOver.

    Set-CsPersistentChatState -Identity "PersistentChatServer:atl-gc-001.litwareinc.com" -PoolState "FailedOver"

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The [Get-CsPersistentChatState](get-cspersistentchatstate.md) cmdlet returns the state of one or more Persistent Chat pools. Persistent Chat pools can be in either the Normal state (in which the pool uses its primary databases) or in a FailedOver state, in which the pool uses its backup databases. You can use the **Set-CsPersistentChatState** cmdlet to change the state of a Persistent Chat pool; when you change the state of the pool, Lync Server 2013 will automatically change the state of each individual server in the pool. To change the state of an individual chat server, use the [Set-CsPersistentChatActiveServer](set-cspersistentchatactiveserver.md) cmdlet.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsPersistentChatState"}

**Lync Server Control Panel:** The functions carried out by the **Set-CsPersistentChatState** cmdlet are not available in the Lync Server Control Panel.

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
<td><p>Suppresses the display of any non-fatal error message that might arise when running the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Service Identity of the Persistent Chat pool where the new service state will be applied. For example:</p>
<p>-Identity PersistentChatServer:atl-persistentchat-001.litwareinc.com</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.PSObject</p></td>
<td><p>Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.</p></td>
</tr>
<tr class="odd">
<td><p><em>PoolState</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PoolState</p></td>
<td><p>Current state of the Persistent Chat pool. Valid values are:</p>
<p>* Normal</p>
<p>* FailedOver</p>
<p>The default value is Normal.</p></td>
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

<span id="InputTypes"></span>

<div>

## Input Types

The **Set-CsPersistentChatState** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatstate object.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

None. Instead, the **Set-CsPersistentChatState** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatState object.

</div>

<div>

## See Also


[Get-CsPersistentChatState](get-cspersistentchatstate.md)  
[Set-CsPersistentChatActiveServer](set-cspersistentchatactiveserver.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

