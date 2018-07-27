---
title: Get-CsUICulture
TOCTitle: Get-CsUICulture
ms:assetid: b8df7083-068b-4d5e-a9b4-448602de6586
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412900(v=OCS.15)
ms:contentKeyID: 48185239
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsUICulture

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Returns information about the culture (that is, the language and regional settings) used by the Lync Server Management Shell. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsUICulture

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 returns basic information about the culture currently in use by the Lync Server Management Shell.

    Get-CsUICulture

</div>

</div>

<div>

## Detailed Description

Although Lync Server is available in multiple languages, the software is not a true MUI (multilingual user interface) application. Among other things, this means that the user interface for the Lync Server Management Shell does not change languages any time you change the operating system language. For example, suppose you have installed the U.S. English version of Lync Server and are also running the Windows operating system under U.S. English. If you change the operating system culture (that is, the language and regional settings) to Danish, the Lync Server Management Shell will not automatically follow suit; instead, the Lync Server Management Shell user interface (including error messages and help text) will remain in U.S. English. If you need to change the culture for the Lync Server Management Shell, you must run the **Set-CsUICulture** cmdlet.

The **Get-CsUICulture** cmdlet provides a way for you to determine the culture currently used in the Lync Server Management Shell.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsUICulture** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins, RTCUniversalReadOnlyAdmins.

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
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>This cmdlet provides only common Windows PowerShell parameters.</p></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Get-CsUICulture** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Get-CsUICulture** cmdlet returns instances of the System.Globalization.CultureInfo class.

</div>

<div>

## See Also


[Set-CsUICulture](set-csuiculture.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

