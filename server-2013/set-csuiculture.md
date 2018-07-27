---
title: Set-CsUICulture
TOCTitle: Set-CsUICulture
ms:assetid: 53fbc126-1df9-4ea0-8055-4e9530ab89d6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398354(v=OCS.15)
ms:contentKeyID: 48184124
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsUICulture

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Enables you to modify the culture (that is, the language and regional settings) used by the Lync Server Management Shell. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsUICulture -Culture <String> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 sets the culture for the Lync Server Management Shell to U.S. English. This is done by using the language code en-US.

    Set-CsUICulture -Culture "en-US"

</div>

<div>

## EXAMPLE 2

Example 2 sets the culture for the Lync Server Management Shell to the default culture value. The default value is the culture setting used when you originally installed Lync Server.

    Set-CsUICulture -Culture "default"

</div>

</div>

<div>

## Detailed Description

Although Lync Server is available in multiple languages, the software is not a true Multilingual User Interface (MUI) application. Among other things, this means that the user interface for the Lync Server Management Shell does not change languages any time you change the operating system language. For example, suppose you have installed the U.S. English version of Lync Server and are also running the Windows operating system under U.S. English. If you change the operating system culture (that is, the language and regional settings) to Danish, the Lync Server Management Shell will not automatically follow suit; instead, the Lync Server Management Shell user interface (including error messages and help text) will remain in U.S. English. If you need to change the culture for the Lync Server Management Shell, you must run the **Set-CsUICulture** cmdlet.

There are two things to keep in mind when using the **Set-CsUICulture** cmdlet. First, the cmdlet can only be used to modify Lync Server Management Shell settings on the local computer; the **Set-CsUICulture** cmdlet cannot change a remote instance of Lync Server Management Shell. This is due to the fact that all the users of a computer share the same instance of the Lync Server Management Shell: allowing a remote user to change the culture would instantly change the culture for any other users of the Lync Server Management Shell, including the local user.

Second, you can only set the language to U.S. English ("en-US") or to the language used when you initially installed Lync Server ("default"). For example, if you originally installed an Italian version of Lync Server, then you have two choices for configuring the UI culture: English or Italian.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsUICulture** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins, RTCUniversalReadOnlyAdmins.

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
<td><p><em>Culture</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to specify the culture used for the Lync Server Management Shell. Set the culture to &quot;en-US&quot; for U.S. English, or set the culture to &quot;default&quot; to use the language used when you originally installed Lync Server.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
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

None. The **Set-CsUICulture** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Set-CsUICulture** cmdlet does not return any values or objects. Instead, the cmdlet modifies existing instances of the System.Globalization.CultureInfo class.

</div>

<div>

## See Also


[Get-CsUICulture](get-csuiculture.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

