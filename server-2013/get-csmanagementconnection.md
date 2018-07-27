---
title: Get-CsManagementConnection
TOCTitle: Get-CsManagementConnection
ms:assetid: b0e2377c-6aab-45d8-b71d-0d37c6f6dae3
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412849(v=OCS.15)
ms:contentKeyID: 48185154
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsManagementConnection

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Returns information about the management connection to the Central Management store. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsManagementConnection

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command in Example 1 returns information about the management connection to the Central Management store.

    Get-CsManagementConnection

</div>

</div>

<div>

## Detailed Description

Configuration data for Lync Server is stored in the Central Management store; it is crucial that both Windows PowerShell and the management replica services be able to locate this database. When you install Lync Server, a service control point is created in Active Directory Domain Services that provides location information for this database. Typically, computers rely on this service control point in order to connect to the Central Management store. To see the details behind this connection (that is, if you want to know which computer the Central Management store is running on, as well information about the SQL Server connection to that Central Management store) you can run the **Get-CsManagementConnection** cmdlet.

If you have used the **Set-CsManagementConnection** cmdlet to set up a temporary management connection for your current instance of Windows PowerShell (for example, in order to work from the local replica), the **Get-CsManagementConnection** cmdlet will report back information for that temporary connection. By comparison, the **Get-CsConfigurationStoreLocation** cmdlet always returns information for the service control point in Active Directory, regardless of where the local management connection is pointed.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsManagementConnection** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins, RTCUniversalReadOnlyAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsManagementConnection"}

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
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>This cmdlet provides only common Windows PowerShell parameters.</p></td>
<td> </td>
<td> </td>
<td> </td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Get-CsManagementConnection** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Get-CsManagementConnection** cmdlet returns instances of the Microsoft.Rtc.Management.Xds.ManagementConnection object.

</div>

<div>

## See Also


[Remove-CsManagementConnection](remove-csmanagementconnection.md)  
[Set-CsManagementConnection](set-csmanagementconnection.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

