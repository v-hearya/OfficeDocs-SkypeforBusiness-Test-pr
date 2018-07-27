---
title: Uninstall-CsDatabase
TOCTitle: Uninstall-CsDatabase
ms:assetid: bd08ac1c-cfcd-4cf8-b082-7d2e83a2837e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412922(v=OCS.15)
ms:contentKeyID: 48185257
ms.date: 07/07/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Uninstall-CsDatabase

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-07-01_

Deletes the specified Lync Server database. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Uninstall-CsDatabase -DatabaseType <Application | Archiving | Monitoring | User | Provision | CentralAdmin | Lyss | Registrar | Edge | PersistentChat | PersistentChatCompliance | CentralMgmt> [-SqlInstanceName <String>] [-SqlServerFqdn <Fqdn>] <COMMON PARAMETERS>

    Uninstall-CsDatabase -CentralManagementDatabase <SwitchParameter> -SqlServerFqdn <Fqdn> [-SqlInstanceName <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Detach <SwitchParameter>] [-Force <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 deletes the Central Management store from the computer atl-sql-001.litwareinc.com.

    Uninstall-CsDatabase -CentralManagementDatabase -SqlServerFqdn atl-sql-001.litwareinc.com 

</div>

<div>

## EXAMPLE 2

In Example 2, the User database is deleted from the computer atl-sql-001.litwareinc.com. When you use the DatabaseType parameter, all stores related to the specified database are deleted.

    Uninstall-CsDatabase -DatabaseType User -SqlServerFqdn atl-sql-001.litwareinc.com 

</div>

</div>

<div>

## Detailed Description

Lync Server makes extensive use of SQL Server databases such as the Central Management store and the Archiving database. These databases are set up at the same time you install Lync Server or at the same time you install a Lync Server role that requires a database back end. After the databases have been installed, you will rarely need to uninstall them.

However, it is possible that you might need to uninstall a Lync Server database at some point; for example, a hardware failure or an issue with network connectivity might make an existing database unusable. Regardless of the reason, the **Uninstall-CsDatabase** cmdlet provides a way for you to remove or detach any of the SQL Server databases used by Lync Server.

Who can run this cmdlet: You must be a member of the domain, a SQL Server administrator, and a local administrator on the computer where SQL Server is installed in order to run the **Uninstall-CsDatabase** cmdlet locally. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Uninstall-CsDatabase"}

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
<td><p>If present, uninstalls the Central Management store. You cannot use both CentralManagementDatabase and DatabaseType in the same command.</p></td>
</tr>
<tr class="even">
<td><p><em>DatabaseType</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.DatabaseNameType</p></td>
<td><p>Database to be deleted. Valid values are:</p>
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
<p>User</p>
<p>To delete the Central Management store, use the CentralManagementDatabase parameter.</p></td>
</tr>
<tr class="odd">
<td><p><em>SqlServerFqdn</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Fully qualified domain name (FQDN) of the computer or SQL Server cluster where the database is located. For example: -SqlServer atl-sql-001.litwareinc.com.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Detach</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>If present, detaches the specified database. When a database is detached, all the file locks imposed by SQL Server are removed. This enables you to directly access the database files in order to do such things as copy those files to another computer.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>If present, forces removal of the database even if that database is currently in use.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report &quot;C:\Logs\UninstallDatabase.html&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>SqlInstanceName</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Name of the database instance containing the database to be removed. A database instance is a set of running processes that provides access to database files.</p></td>
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

None. The **Uninstall-CsDatabase** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Uninstall-CsDatabase** cmdlet does not return any values or objects.

</div>

<div>

## See Also


[Install-CsDatabase](install-csdatabase.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

