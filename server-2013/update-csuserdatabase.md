---
title: Update-CsUserDatabase
TOCTitle: Update-CsUserDatabase
ms:assetid: 86ed4291-70cc-4c41-ab2a-e5f7546a0f1f
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398682(v=OCS.15)
ms:contentKeyID: 48184715
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Update-CsUserDatabase

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Forces the back-end user database to clear its replication status with Active Directory. This causes the database to re-read all the user-related information stored in Active Directory Domain Services. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Update-CsUserDatabase [-Force <SwitchParameter>] [-Fqdn <Fqdn>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 locates the user database for the pool where the local computer is located, then forces that database to connect to and return complete user information from Active Directory.

    Update-CsUserDatabase

</div>

<div>

## EXAMPLE 2

Example 2 shows how you can force a specific user database to re-read data from Active Directory. In this case, that’s the user database for the pool atl-cs-001.litwareinc.com.

    Update-CsUserDatabase -Fqdn atl-cs-001.litwareinc.com

</div>

</div>

<div>

## Detailed Description

The Lync Server user database holds detailed information about such things as contacts, groups, and access permissions. As such, the database is required to periodically synch its contents with the information stored in Active Directory.

More often than not, the automatic synch between the user database and Active Directory will keep the information in the user database up to date. However, it is possible that a problem might occur that prevents this automatic synchronization from taking place. In a case such as that, you can use the **Update-CsUserDatabase** cmdlet to force the user database to refresh its contents by re-reading all of the user information stored in Active Directory. You might also need to run this cmdlet if a product update ever includes a change to the user replicator service.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Update-CsUserDatabase** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself) run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Update-CsUserDatabase"}

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
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might arise when running the command.</p></td>
</tr>
<tr class="even">
<td><p><em>Fqdn</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Fully qualified domain name (FQDN) of the computer hosting the user database. If this parameter is not specified then the <strong>Update-CsUserDatabase</strong> cmdlet will update the user database for the pool that the local computer belongs to.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Update-CsUserDatabase** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

None. Instead, the **Update-CsUserDatabase** cmdlet updates instances of the Microsoft.Rtc.Management.Xds.DisplayuserDatabase object.

</div>

<div>

## See Also


[Get-CsUserDatabaseState](get-csuserdatabasestate.md)  
[Set-CsUserDatabaseState](set-csuserdatabasestate.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

