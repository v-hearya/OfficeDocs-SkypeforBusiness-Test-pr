---
title: Import-CsConfiguration
TOCTitle: Import-CsConfiguration
ms:assetid: 9a9c27f2-313c-4327-aeed-c47852a831ec
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398800(v=OCS.15)
ms:contentKeyID: 48184889
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Import-CsConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Imports your Lync Server topology, policies, and configuration settings to either the Central Management store or to the local computer. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Import-CsConfiguration -ByteInput <Byte[]> <COMMON PARAMETERS>

    Import-CsConfiguration -FileName <String> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 imports the current topology, configuration settings, and policies from a file named C:\\Config.zip to the Central Management store.

    Import-CsConfiguration -FileName "C:\Config.zip"

</div>

<div>

## EXAMPLE 2

Example 2 shows how data can be initially replicated to a computer located in the perimeter network. In this example, configuration data has been exported to a file named Config.zip; this file has then been copied to the C:\\ folder on the computer located in the perimeter network. Import-CsConfiguration is then used to import that data, with the LocalStore parameter causing that data to be imported to the local computer instead of the Central Management store.

    Import-CsConfiguration -FileName "C:\Config.zip" -LocalStore

</div>

<div>

## EXAMPLE 3

The two commands shown in Example 3 export the current topology, configuration settings, and policies and then import that data to the local computer, all without using a .ZIP file. To do this, the first command uses the **Export-CsConfiguration** cmdlet and the AsBytes parameter to export the current topology, configuration settings, and policies as a byte array; this byte array is stored in a variable named $x. In the second command, the **Import-CsConfiguration** cmdlet and the ByteInput parameter are used to import the information stored in $x. The LocalStore parameter causes the data to be imported to the local computer instead of the Central Management store. The net effect is that data is copied from the Central Management store to the local computer.

    $x = Export-CsConfiguration -AsBytes
    Import-CsConfiguration -ByteInput $x -LocalStore

</div>

</div>

<div>

## Detailed Description

Computers that run Lync Server services or server roles must have a copy of the current topology, current configuration settings, current policies, and so on before they can function in their appointed role. Lync Server is responsible for ensuring that this information is passed along to each computer that needs it.

The Import-CsConfiguration cmdlet and Export-CsConfiguration cmdlet are used to backup and restore your Lync Server topology, configuration settings, and policies during a Central Management store upgrade. The **Export-CsConfiguration** cmdlet enables you to export data to a .ZIP file; you can then use the **Import-CsConfiguration** cmdlet to read that .ZIP file and restore the topology, settings, and policies to the Central Management store. After that, Lync Server’s replication services will replicate the restored information to computers running services.

The ability to export and import configuration data is also used when initially configuring computers located in your perimeter network (for example, Edge Server). When configuring a computer located in the perimeter network, you must first perform a manual replication using the CsConfiguration cmdlets: you will need to export the configuration data using the **Export-CsConfiguration** cmdlet and then copy the .ZIP file to the computer in the perimeter network. After that, you can use the **Import-CsConfiguration** cmdlet and the LocalStore parameter to import the data. You only need to do this once; after that, replication will take place automatically.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Import-CsConfiguration** cmdlet locally: RTCUniversalServerAdmins. In addition to being a member of RTCUniversalServerAdmins, you must also be a local administrator or have local configuration replicator permissions to run this cmdlet. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Import-CsConfiguration"}

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
<td><p><em>ByteInput</em></p></td>
<td><p>Required</p></td>
<td><p>System.Byte[]</p></td>
<td><p>Reads topology information from a byte array stored in a variable. This byte array is created by using the ByteInput parameter when calling the <strong>Export-CsConfiguration</strong> cmdlet.</p>
<p>You cannot use both the ByteInput parameter and the FileName parameter in the same command.</p></td>
</tr>
<tr class="even">
<td><p><em>FileName</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Path to the .ZIP file created by Export-CsConfiguration. For example: -FileName &quot;C:\Config.zip&quot;. Note that you must include either the FileName or the ByteInput parameter, but not both, when calling the <strong>Import-CsConfiguration</strong> cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Bypasses any prompts that would otherwise appear should a non-fatal error occur when running the command. To set the Force parameter to True, use this syntax:</p>
<p>-Force:$True</p></td>
</tr>
<tr class="even">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Copies the configuration data to the local computer rather than the Central Management store.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Import-CsConfiguration** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Import-CsConfiguration** cmdlet does not return any values or objects.

</div>

<div>

## See Also


[Export-CsConfiguration](export-csconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

