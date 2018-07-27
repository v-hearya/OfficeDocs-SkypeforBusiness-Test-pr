---
title: Export-CsConfiguration
TOCTitle: Export-CsConfiguration
ms:assetid: 7da7e133-e405-466c-a852-06a4fb678c59
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398627(v=OCS.15)
ms:contentKeyID: 48184614
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Export-CsConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Exports your Lync Server topology, policies, and configuration settings to a file. Among other things, this file can then be used to restore this information to the Central Management store after an upgrade, a hardware failure, or some other issue has resulted in data loss. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Export-CsConfiguration [-AsBytes <SwitchParameter>] <COMMON PARAMETERS>

    Export-CsConfiguration -FileName <String> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 exports Lync Server data from the Central Management store to a file named C:\\Config.zip.

    Export-CsConfiguration -FileName "C:\Config.zip"

</div>

</div>

<div>

## Detailed Description

Computers that run Lync Server services or server roles must have a copy of the current topology, current configuration settings, and current policies before they can function in their appointed role. Lync Server is responsible for ensuring that this information is passed along to each computer that needs it.

The **Export-CsConfiguration** cmdlet and the **Import-CsConfiguration** cmdlet are used to backup and restore your Lync Server topology, configuration settings, and policies during a Central Management store upgrade. The **Export-CsConfiguration** cmdlet enables you to export data to a .ZIP file; you can then use the **Import-CsConfiguration** cmdlet to read that .ZIP file and restore the topology, configuration settings, and policies to the Central Management store. After that, the replication services of Lync Server will replicate the restored information to other computers running Lync Server services.

The ability to export and import configuration data is also used when initially configuring computers located in your perimeter network (for example, Edge Servers). When configuring a computer in the perimeter network, you must first perform a manual replication using the CsConfiguration cmdlets: you will need to export the configuration data using the **Export-CsConfiguration** cmdlet and then copy the .ZIP file to the computer in the perimeter network. After that, you can use the **Import-CsConfiguration** cmdlet and the LocalStore parameter to import the data. You only need to do this once; after that, replication will take place automatically.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Export-CsConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Export-CsConfiguration"}

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
<td><p><em>FileName</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Path to the .ZIP file to be created when you run the <strong>Export-CsConfiguration</strong> cmdlet. For example: -FileName &quot;C:\Config.zip&quot;. Note that you must include either the FileName or the AsBytes parameters, but not both, when calling the <strong>Export-CsConfiguration</strong> cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>AsBytes</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Returns topology information as a byte array; the returned data must then be stored in a variable in order to be used by the <strong>Import-CsConfiguration</strong> cmdlet. You cannot use both AsBytes and FileName in the same command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command. To set the Force parameter to True use this syntax:</p>
<p>-Force:$True</p></td>
</tr>
<tr class="even">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the configuration data from the local computer rather than from the Central Management store itself.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Export-CsConfiguration** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

If called along with the AsBytes parameter, the **Export-CsConfiguration** cmdlet returns configuration information in the form of a byte array.

</div>

<div>

## See Also


[Import-CsConfiguration](import-csconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

