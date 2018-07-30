---
title: Remove-CsCallParkOrbit
TOCTitle: Remove-CsCallParkOrbit
ms:assetid: b8e7c236-f8de-45bd-966b-60c815b37aed
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412901(v=OCS.15)
ms:contentKeyID: 48185212
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsCallParkOrbit

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Removes a specific call park orbit range. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsCallParkOrbit -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

In this example, the **Remove-CsCallParkOrbit** cmdlet is used to delete the call park orbit range with the name Redmond CPO 1.

    Remove-CsCallParkOrbit -Identity "Redmond CPO 1"

</div>

<div>

## EXAMPLE 2

The command in this example removes all call park orbit ranges that have been defined for an organization. The command first calls the **Get-CsCallParkOrbit** cmdlet with no parameters to retrieve all the defined call park orbit ranges. It then pipes that collection of call park orbit ranges to the **Remove-CsCallParkOrbit** cmdlet, which removes each call park orbit.

    Get-CsCallParkOrbit | Remove-CsCallParkOrbit

</div>

<div>

## EXAMPLE 3

This command removes all call park orbit ranges that have an identity that includes the string "Redmond", such as "Redmond 501", "CP Redmond 1", and "ARedmond". The command first calls the **Get-CsCallParkOrbit** cmdlet with the Filter parameter to retrieve all call park orbit ranges that have an Identity with the string Redmond in it. This collection is piped to the **Remove-CsCallParkOrbit** cmdlet, which removes everything in the collection.

    Get-CsCallParkOrbit -Filter *Redmond* | Remove-CsCallParkOrbit

</div>

</div>

<div>

## Detailed Description

The **Remove-CsCallParkOrbit** cmdlet deletes the call park orbit range with the name passed to the Identity parameter (this parameter is required). Each call park orbit within an organization must have a unique range of numbers. Removing a call park orbit frees up the range that was in that call park orbit. The freed numbers can then be used in a newly defined call park orbit.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsCallParkOrbit** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsCallParkOrbit"}

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
<td><p>The name of the call park orbit range. This name was assigned by the administrator when the call park orbit range was defined.</p></td>
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

Microsoft.Rtc.Management.Voice.Helpers.DisplayCallParkOrbit object. Accepts pipelined input of call park orbit objects.

</div>

<div>

## Return Types

This cmdlet does not return a value. It removes an object of type Microsoft.Rtc.Management.Voice.Helpers.DisplayCallParkOrbit.

</div>

<div>

## See Also


[New-CsCallParkOrbit](new-cscallparkorbit.md)  
[Set-CsCallParkOrbit](set-cscallparkorbit.md)  
[Get-CsCallParkOrbit](get-cscallparkorbit.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

