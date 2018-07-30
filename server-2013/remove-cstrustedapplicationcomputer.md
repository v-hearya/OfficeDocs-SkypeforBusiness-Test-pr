---
title: Remove-CsTrustedApplicationComputer
TOCTitle: Remove-CsTrustedApplicationComputer
ms:assetid: c9c0604b-a94e-42b9-9db3-bc3dbe686e41
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398838(v=OCS.15)
ms:contentKeyID: 48185433
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsTrustedApplicationComputer

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Removes a trusted application computer. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsTrustedApplicationComputer -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example removes the computer with the FQDN Trust1.litwareinc.com.

    Remove-CsTrustedApplicationComputer -Identity Trust1.litwareinc.com

</div>

<div>

## EXAMPLE 2

This example removes all trusted computers that have FQDNs beginning with the string Trust. The example begins by calling the **Get-CsTrustedApplicationComputer** cmdlet, passing the Filter parameter the value Trust\*. This will retrieve all trusted application computers with an FQDN beginning with Trust and ending with any set of characters. That collection of computers is then piped to the **Remove-CsTrustedApplicationComputer** cmdlet, which removes each item (each computer) in the collection. Keep in mind that this won’t remove the computers from a pool if removing those computers would result in an empty pool.

    Get-CsTrustedApplicationComputer -Filter Trust* | Remove-CsTrustedApplicationComputer

</div>

</div>

<div>

## Detailed Description

It is recommended that the computers that are running trusted applications within a Lync Server deployment be added to a separate pool that is only for trusted applications. However, you can add trusted application computers to an existing pool that is also used for other purposes. Use this cmdlet to remove a trusted application computer.

When you use this cmdlet to remove a trusted application computer, it will be removed not only from the list of trusted application computers but from the list of computers available on Lync Server. In other words, if you call the **Get-CsTrustedApplicationComputer** cmdlet or the **Get-CsComputer** cmdlet the computer will no longer be listed. You cannot remove a trusted application computer if it’s the only computer on the pool. If you want to remove the only computer on a pool you must remove the entire pool (which can be done by calling the **Remove-CsTrustedApplicationPool** cmdlet).

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsTrustedApplicationComputer** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsTrustedApplicationComputer"}

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
<td><p>The fully qualified domain name (FQDN) of the computer to remove.</p></td>
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

Microsoft.Rtc.Management.Xds.DisplayComputer object. Accepts pipelined input of trusted application computer objects.

</div>

<div>

## Return Types

This cmdlet does not return a value. It removes an object of type Microsoft.Rtc.Management.Xds.DisplayComputer.

</div>

<div>

## See Also


[New-CsTrustedApplicationComputer](new-cstrustedapplicationcomputer.md)  
[Get-CsTrustedApplicationComputer](get-cstrustedapplicationcomputer.md)  
[Remove-CsTrustedApplicationPool](remove-cstrustedapplicationpool.md)  
[Get-CsTrustedApplicationPool](get-cstrustedapplicationpool.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

