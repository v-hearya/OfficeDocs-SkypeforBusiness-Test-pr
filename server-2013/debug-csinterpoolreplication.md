---
title: Debug-CsInterPoolReplication
TOCTitle: Debug-CsInterPoolReplication
ms:assetid: 945bfd1c-1759-4869-9316-b3260fcc633d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ619185(v=OCS.15)
ms:contentKeyID: 49733743
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Debug-CsInterPoolReplication

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-06-04_

Verifies that replication is working between a Registrar pool and its assigned backup pool. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Debug-CsInterPoolReplication -PoolFqdn <Fqdn> [-BackupModule <All | CentralMgmt | PresenceFocus | DataConf>] [-Force <SwitchParameter>]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 verifies the full replication status between the pool atl-cs-001.litwareinc.com and its previously-assigned backup pool.

    Debug-CsInterPoolReplication -PoolFqdn "atl-cs-001.litwareinc.com"

</div>

<div>

## Example 2

In Example 2, only the replication of data conferencing data is verified between the pool atl-cs-001.litwareinc.com and its previously-assigned backup pool.

    Debug-CsInterPoolReplication -PoolFqdn "atl-cs-001.litwareinc.com" -BackupModule DataConf

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

In Lync Server 2013 each Registrar pool can be associated with a backup pool. The backup pool maintains a copy of all the data stored on the primary pool. Should the primary pool become unavailable then users of that pool can automatically be "failed over" to the backup pool. This enables those users to continue to use Lync Server even though their home pool is not available. The Debug-CsInterPoolReplication cmdlet is used to compare the data stores on a primary pool and its backup pool, and thus verify that replication between the two pools is working as expected.

Note that this command will fail if the pool being tested has not been assigned a backup pool.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Debug-CsInterPoolReplication"}

**Lync Server Control Panel:** The functions carried out by the Debug-CsInterPoolReplication cmdlet are not available in the Lync Server Control Panel.

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
<td><p>Fully qualified domain name of the primary pool being tested. For example:</p>
<p>-PoolFqdn &quot;atl-cs-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>BackupModule</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Hadr.BackupService.BackupModules</p></td>
<td><p>Enables administrators to specify the data store to be verified. Allowed values are:</p>
<p>* All</p>
<p>* CentralMgmt</p>
<p>* PresenceFocus</p>
<p>* DataConf</p>
<p>The default value is All.</p></td>
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

None. Debug-CsInterPoolReplication does not accept pipelined data.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

String value.

</div>

</div>

<span> </span>

</div>

</div>

</div>

