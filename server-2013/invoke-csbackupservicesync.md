---
title: Invoke-CsBackupServiceSync
TOCTitle: Invoke-CsBackupServiceSync
ms:assetid: f3de25c2-a1ef-4781-8b33-74f5dc1e6f8d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205374(v=OCS.15)
ms:contentKeyID: 48185796
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Invoke-CsBackupServiceSync

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Manually invokes backup synchronization between a Lync Server 2013 pool and its designated backup pool. This allows administrators to synchronize data without waiting for Lync Server replication. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Invoke-CsBackupServiceSync -PoolFqdn <Fqdn> [-BackupModule <String>] [-Force <SwitchParameter>]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 synchronizes the backup services for the pool atl-cs-001.litwareinc.com.

    Invoke-CsBackupServiceSync -PoolFqdn "atl-cs-001.litwareinc.com"

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The **Invoke-CsBackupServiceSync** cmdlet enables administrators to synchronize the data between a Registrar pool and its backup pool. The **Invoke-CsBackupServiceSync** cmdlet will only copy as much data as needed in order to bring the two pools into sync.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Invoke-CsBackupServiceSync"}

**Lync Server Control Panel:** The functions carried out by the **Invoke-CsBackupServiceSync** cmdlet are not available in the Lync Server Control Panel.

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
<td><p><em>PoolFqdn</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Fully qualified domain name of the pool where backup service synchronization is being invoked. For example:</p>
<p>-PoolFqdn &quot;atl-cs-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>BackupModule</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Indicates the type of data to be synchronized. Valid values are:</p>
<p>* UserServices.PresenceFocus</p>
<p>* ConfServices.DataConf</p>
<p>* CentralMgmt.CMSMaster</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
</tbody>
</table>


</div>

<span id="InputTypes"></span>

<div>

## Input Types

String value. The **Invoke-CsBackupServiceSync** cmdlet can accept a pipelined string value representing the fully qualified domain name of a Lync Server 2013 pool.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

None.

</div>

<div>

## See Also


[Backup-CsPool](backup-cspool.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

