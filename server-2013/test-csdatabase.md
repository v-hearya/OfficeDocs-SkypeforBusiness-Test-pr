---
title: Test-CsDatabase
TOCTitle: Test-CsDatabase
ms:assetid: 4165f1e1-fe64-45e7-a13f-f23c0205f386
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204839(v=OCS.15)
ms:contentKeyID: 48183971
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Test-CsDatabase

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-06-05_

Tests the configuration of the Lync Server 2013 databases. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Test-CsDatabase -LocalService <SwitchParameter> <COMMON PARAMETERS>

    Test-CsDatabase -CentralManagementDatabase <SwitchParameter> [-SqlInstanceName <String>] [-SqlServerFqdn <Fqdn>] <COMMON PARAMETERS>

    Test-CsDatabase -ConfiguredDatabases <SwitchParameter> -SqlServerFqdn <Fqdn> <COMMON PARAMETERS>

    Test-CsDatabase -DatabaseType <Application | Archiving | Monitoring | User | Provision | CentralAdmin | Lyss | Registrar | Edge | PersistentChat | PersistentChatCompliance | CentralMgmt> -SqlServerFqdn <Fqdn> [-SqlInstanceName <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Report <String>] [-WhatIf [<SwitchParameter>]]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 verifies the configuration of the Central Management database.

    Test-CsDatabase -CentralManagementDatabase

</div>

<div>

## Example 2

Example 2 verifies all the Lync Server databases installed on the computer atl-sql-001.litwareinc.com.

    Test-CsDatabase -ConfiguredDatabases -SqlServerFqdn "atl-sql-001.litwareinc.com"

</div>

<div>

## Example 3

In Example 3, verification is performed only for the Archiving database installed on the computer atl-sql-001.litwareinc.com. Note that the SqlInstanceName parameter is included to specify the SQL Server instance (Archinst) where the Archiving database is located.

    Test-CsDatabase -DatabaseType "Archiving" -SqlServerFqdn "atl-sql-001.litwareinc.com" -SqlInstanceName "archinst"

</div>

<div>

## Example 4

The command shown in Example 4 verifies the databases installed on the local computer.

    Test-CsDatabase -LocalService

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The **Test-CsDatabase** cmdlet verifies connectivity to one or more Lync Server 2013 databases. When run, the **Test-CsDatabase** cmdlet reads the Lync Server topology, attempts to connect each of the relevant databases, and then reports back the success or failure of each attempt. If a connection can be made, the cmdlet will also report back such information as the database name, SQL Server version information, and the location of any installed mirror databases.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsDatabase"}

**Lync Server Control Panel:** The functions carried out by the **Test-CsDatabase** cmdlet are not available in the Lync Server Control Panel.

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
<td><p><em>CentralManagementDatabase</em></p></td>
<td><p>Required</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Tests the configuration of the Central Management database. This parameter cannot be used in conjunction with the ConfiguredDatabases parameter or the DatabaseType parameter.</p></td>
</tr>
<tr class="even">
<td><p><em>ConfiguredDatabases</em></p></td>
<td><p>Required</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Tests the configuration of all the Lync Server databases installed on the specified computer. You must include the SqlServerFqdn parameter when using the ConfiguredDatabases parameter. In addition, this parameter cannot be used in the same command as the CentralManagementDatabase or the DatabaseType parameters.</p></td>
</tr>
<tr class="odd">
<td><p><em>DatabaseType</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.DatabaseNameType</p></td>
<td><p>Type of database to be validated. Allowed values are:</p>
<p>Valid values for DatabaseType are:</p>
<p>Application</p>
<p>Archiving</p>
<p>CentralAdmin</p>
<p>CentralMgmt</p>
<p>Edge</p>
<p>Lyss</p>
<p>Monitoring</p>
<p>PersistentChat</p>
<p>PersistentChatCompliance</p>
<p>Provision</p>
<p>Registrar</p>
<p>User</p></td>
</tr>
<tr class="even">
<td><p><em>LocalService</em></p></td>
<td><p>Required</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Validates all the databases used by any of the Lync Server services that are installed on the local computer. This includes not only locally-installed databases but also databases installed on remote computers, provided those databases are used by one or more local services.</p></td>
</tr>
<tr class="odd">
<td><p><em>SqlServerFqdn</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Fully qualified domain name of the computer whether the databases to be validated are installed.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to specify a file path for the log file created when the cmdlet runs. For example:</p>
<p>-Report &quot;C:\Logs\TestDatabases.html&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>SqlInstanceName</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>SQL Server instance where the databases to be validated are installed. For example:</p>
<p>-SqlInstanceName &quot;rtc&quot;</p></td>
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

<span id="InputTypes"></span>

<div>

## Input Types

None. The **Test-CsDatabase** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **Test-CsDatabase** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.

</div>

<div>

## See Also


[Get-CsDatabaseMirrorState](get-csdatabasemirrorstate.md)  
[Get-CsService](get-csservice.md)  
[Get-CsUserDatabaseState](get-csuserdatabasestate.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

