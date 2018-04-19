---
title: Set-CsPstnUsage
TOCTitle: Set-CsPstnUsage
ms:assetid: ecba9ed6-4845-4035-933e-0c540d530b72
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg399069(v=OCS.15)
ms:contentKeyID: 48185753
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsPstnUsage

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-07_

Modifies a set of strings that identify the allowed public switched telephone network (PSTN) usages. This cmdlet can be used to add usages to the list of PSTN usages or remove usages from the list. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsPstnUsage [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsPstnUsage [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Usage <PSListModifier>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This command adds the string "International" to the current list of available PSTN usages.

    Set-CsPstnUsage -Identity global -Usage @{add="International"}

</div>

<div>

## EXAMPLE 2

This command removes the string "Local" from the list of available PSTN usages.

    Set-CsPstnUsage -Identity global -Usage @{remove="Local"}

</div>

<div>

## EXAMPLE 3

The command in this example performs the exact same action as the command in Example 2: it removes the "Local" PSTN usage. This example shows the command without the Identity parameter specified. The only Identity available to the **Set-CsPstnUsage** cmdlet is the Global identity; omitting the Identity parameter defaults to Global.

    Set-CsPstnUsage -Usage @{remove="Local"}

</div>

<div>

## EXAMPLE 4

This command replaces everything in the usage list with the values International and Restricted. All previously existing usages are removed.

    Set-CsPstnUsage -Usage @{replace="International","Restricted"}

</div>

</div>

<div>

## Detailed Description

PSTN usages are string values that are used for call authorization. A PSTN usage links a voice policy to a route. The **Set-CsPstnUsage** cmdlet is used to add or remove phone usages to or from the usage list. This list is global so it can be used by policies and routes throughout the Lync Server deployment.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsPstnUsage** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsPstnUsage"}

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
<td><p>Suppresses any confirmation prompts that would otherwise be displayed before making changes.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>The scope at which these settings are applied. The Identity for this cmdlet is always Global.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Optional</p></td>
<td><p>PstnUsages</p></td>
<td><p>A reference to a PSTN usage object. This object must be of type PstnUsages and can be retrieved by calling the <strong>Get-CsPstnUsage</strong> cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><em>Usage</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>Contains a list of allowable usage strings. These entries can be any string value.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.PstnUsages object. Accepts pipelined input of PSTN usage objects.

</div>

<div>

## Return Types

This cmdlet does not return a value or object. Instead, it configures instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.PstnUsages object.

</div>

<div>

## See Also


[Get-CsPstnUsage](get-cspstnusage.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

