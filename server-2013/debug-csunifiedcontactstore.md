---
title: Debug-CsUnifiedContactStore
TOCTitle: Debug-CsUnifiedContactStore
ms:assetid: 8e92d262-604d-41b1-9530-947765025a79
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ994054(v=OCS.15)
ms:contentKeyID: 51803965
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Debug-CsUnifiedContactStore

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-04-17_

Verifies whether the contacts for a user (or group of users) are stored in the unified contacts store.

This cmdlet was introduced in the Cumulative Updates for Lync Server 2013: February 2013.

<div>

## Syntax

    Debug-CsUnifiedContactStore -Identity <UserIdParameter> [-ContactDataExportFileName <String>] <COMMON PARAMETERS>

    Debug-CsUnifiedContactStore -PoolFqdn <Fqdn> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 verifies the unified contact store status for all the users who have accounts homed on the pool atl-cs-001.litwareinc.com.

    Debug-CsUnifiedContactStore -PoolFqdn "atl-cs-001.litwareinc.com"

</div>

<div>

## Example 2

In Example 2, the unified contact store status is verified for a single user: the user with the SIP address "kenmyer@litwareinc.com".

    Debug-CsUnifiedContactStore -Identity "kenmyer@litwareinc.com"

</div>

</div>

<div>

## Detailed Description

The unified contact store (introduced in Lync Server 2013 enables users to access their contact list from multiple applications, including Microsoft Lync 2013, Outlook 2013, and Outlook Web App. This access is made available by storing contact information in a single location: Microsoft Exchange Server 2013.

The **Debug-CsUnifiedContactStore** cmdlet enables administrators to verify whether a specific user or a specific set of users (that is, all the users with accounts homed in a particular pool) have their contact lists stored in the unified contact store. If you run the **Debug-CsUnifiedContactStore** cmdlet against a specific user account, the cmdlet will indicate whether that user’s contacts have been moved for the unified contact store, the number of attempts that have been made to move those contacts, and the date and time when Lync Server last tried to migrate the contact list. When called against a pool, the **Debug-CsUnifiedContactStore** cmdlet returns data similar to this:

FrontEnd: atl-cs-001.litwareinc.com  
UcsDisabledCount: 44  
UcsAllowedCount: 129  
UcsMigratingCount: 11  
UcsMigratedCount:  
FailedUserData:

The **Debug-CsUnifiedContactStore** cmdlet, and the ContactDataExportFileName parameter, can also be used to export contact information for a user to an XML file.

To return a list of all the role-based access control (RBAC) roles that this cmdlet has been assigned to (including any custom RBAC roles that you have created), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Debug-CsUnifiedContactStore"}

**Lync Server Control Panel:** The functions carried out by the **Debug-CsUnifiedContactStore** cmdlet are not available in the Lync Server Control Panel.

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
<td><p><em>Identity</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>SIP address of an individual user whose unified contact store status is being verified. (You can specify only one user per command.) For example:</p>
<p>-Identity &quot;kenmyer@litwareinc.com&quot;</p>
<p>When specifying the SIP address, the sip: prefix is optional. This syntax will also work:</p>
<p>-Identity &quot;sip:kenmyer@litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>PoolFqdn</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Fully qualified domain name of the Registrar pool whose unified contact store status is being verified. All user accounts homed on the specified pool will be checked. For example:</p>
<p>-PoolFqdn &quot;atl-cs-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>ContactDataExportFileName</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>File path for the XML file that will contain the contacts for the specified user when those contacts exported from the unified contact store. For example:</p>
<p>-ContactDataExportFileName &quot;C:\Exports\KenMyer.xml&quot;</p>
<p>Note that you must include the Identity parameter and the SIP address for the user whose contacts you want to export. If that user has not been enabled for the unified contact store, the command will terminate and no contacts will be exported.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any nonfatal error message that might occur when running the command.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Debug-CsUnifiedContactStore** cmdlet does not accept pipelined data.

</div>

<div>

## Return Types

The **Debug-CsUnifiedContactStore** cmdlet returns instances of the Microsoft.Rtc.Management.Presence.Cmdlets.GetUcsFrontEndData object.

</div>

<div>

## See Also


[Test-CsUnifiedContactStore](test-csunifiedcontactstore.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

