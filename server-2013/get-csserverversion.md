---
title: Get-CsServerVersion
TOCTitle: Get-CsServerVersion
ms:assetid: 66af07c0-fdfe-491a-ad48-b8821fb58904
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398470(v=OCS.15)
ms:contentKeyID: 48184338
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsServerVersion

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-07_

Returns server licensing information for a computer running Lync Server. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsServerVersion

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 returns licensing information for the local computer. This is the only way that the **Get-CsServerVersion** cmdlet can be used.

    Get-CsServerVersion

</div>

</div>

<div>

## Detailed Description

Lync Server comes in two different versions: an evaluation version (which will eventually expire) and a fully-licensed version. The **Get-CsServerVersion** cmdlet provides a way for administrators to determine which version of Lync Server is running on a computer. The **Get-CsServerVersion** cmdlet, which is designed to run only on the local computer and which has no additional parameters, attempts to read the registry value HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Real-Time Communications\\{A593FD00-64F1-4288-A6F4-E699ED9DCA35}\\Type. Based on that registry value, the cmdlet will then report back the version number of the software and the Lync Server licensing information. That licensing information will tell you one of the following:

That the evaluation license key has been installed.

That the volume license key has been installed.

That no license key is required for the components installed on the local computer. (Licensing is required only for computers functioning as a Front End Server, a Director, or an Edge Server.)

If an error occurs, the **Get-CsServerVersion** cmdlet will report that the license type and version information could not be retrieved, and recommend that you reinstall the Lync Server components.

Note that Get-CsServerVersion returns only the base version number. For example, Get-CsServerVersion will return a value such as 5.0.8308 even if an update has officially changed the version number to 5.0.8308.291. If you need a very specific version number then you should use the Windows Control Panel.

</div>

<div>

## Parameters


<table>
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
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Get-CsServerVersion** cmdlet does not support pipelined input.

</div>

<div>

## Return Types

The **Get-CsServerVersion** cmdlet returns a string value.

</div>

</div>

<span> </span>

</div>

</div>

</div>

