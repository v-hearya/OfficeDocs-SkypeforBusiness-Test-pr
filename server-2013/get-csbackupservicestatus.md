---
title: Get-CsBackupServiceStatus
TOCTitle: Get-CsBackupServiceStatus
ms:assetid: 7f56cc81-534c-48e8-9f74-5741d4534a83
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205032(v=OCS.15)
ms:contentKeyID: 48184630
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsBackupServiceStatus

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-12-13_

Returns information about the current state of the backup service for a specified pool. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Get-CsBackupServiceStatus -PoolFqdn <Fqdn> [-Category <UserData | CMS>] [-Force <SwitchParameter>]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The preceding command returns the backup service status for the pool atl-cs-001.litwareinc.com.

    Get-CsBackupServiceStatus -PoolFqdn "atl-cs-001.litwareinc.com"

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The **Get-CsBackupServiceStatus** cmdlet enables administrators to verify that the backup service for a specified Registrar pool has been configured and is working properly. Note that, by default, only users who belong to the RTCUniversalServerAdmins group are allowed to run this cmdlet and check the backup status for a pool. To provide additional groups with permission to run the cmdlet, use the **Set-CsBackupServiceConfiguration** cmdlet to add those groups to the AuthorizedUniversalGroups property.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsBackupServiceStatus"}

**Lync Server Control Panel:** The functions carried out by the **Get-CsBackupServiceStatus** cmdlet are not available in the Lync Server Control Panel.

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
<td><p>Fully qualified domain name of the pool whose backup service status is being checked. For example:</p>
<p>-PoolFqdn &quot;atl-cs-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Category</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Hadr.BackupService.BackupCategory</p></td>
<td><p>Type of backup whose status is being checked. Allowed values are:</p>
<p>* CMS</p>
<p>* UserData</p>
<p>If this parameter is not specified then both backup types will be checked.</p></td>
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

None. The **Get-CsBackupServiceStatus** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

Returns information about the backup service.

</div>

<div>

## See Also


[Get-CsBackupServiceConfiguration](get-csbackupserviceconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

