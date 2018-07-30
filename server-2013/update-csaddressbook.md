---
title: Update-CsAddressBook
TOCTitle: Update-CsAddressBook
ms:assetid: 109c5fe7-0154-4161-b19f-01bab024bb3d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398194(v=OCS.15)
ms:contentKeyID: 48183433
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Update-CsAddressBook

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-20_

Forces the specified Address Book servers to synchronize their contents with the User database. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Update-CsAddressBook [-Force <SwitchParameter>] [-Fqdn <Fqdn>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

In Example 1, the **Update-CsAddressBook** cmdlet is called without any parameters. This synchronizes all the Address Book servers in the organization.

    Update-CsAddressBook

</div>

<div>

## EXAMPLE 2

In Example 2, only a single Address Book server is synchronized: the server with the FQDN atl-abs-001.litwareinc.com.

    Update-CsAddressBook -Fqdn atl-abs-001.litwareinc.com

</div>

</div>

<div>

## Detailed Description

Address Book servers are intermediaries between Active Directory and Lync Server. The Address Book server ensures that the user information stored in Lync Server is in synch with the user information stored in Active Directory. This is done by periodically synching Address Book files with the information stored in the User database. By default, this synchronization takes place every five minutes. (However, that time interval can be modified by using the **Set-CsAddressBookConfiguration** cmdlet.)

If you can’t wait for synchronization to take place or if it appears that, for some reason, synchronization isn’t taking place, you can use the **Update-CsAddressBook** cmdlet to force an Address Book server to immediately synch with the user information stored in the User database.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Update-CsAddressBook** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Update-CsAddressBook"}

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
<td><p>Suppresses any confirmation prompts or non-fatal error messages that might occur when you run the cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>Fqdn</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Enables you to specify an individual Address Book to be updated. If this parameter is not included then all of your Address Book servers will be synchronized with the User database. Individual Address Book servers should be referenced by their fully qualified domain name (FQDN); for example, atl-abs-001.litwareinc.com.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Update-CsAddressBook** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

None. Instead, the **Update-CsAddressBook** cmdlet updates existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.AddressBook.AddressBookSettings object.

</div>

<div>

## See Also


[Get-CsAddressBookConfiguration](get-csaddressbookconfiguration.md)  
[Test-CsAddressBookService](test-csaddressbookservice.md)  
[Test-CsAddressBookWebQuery](test-csaddressbookwebquery.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

