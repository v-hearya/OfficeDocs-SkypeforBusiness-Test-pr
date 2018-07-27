---
title: Get-CsOnlineUser
TOCTitle: Get-CsOnlineUser
ms:assetid: 2bfafd70-a7d9-4308-a353-5ecf44249b53
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ994026(v=OCS.15)
ms:contentKeyID: 51803935
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsOnlineUser

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Returns information about users who have accounts homed on Microsoft Lync Online. This cmdlet can only be used with Lync Online.

<div>

## Syntax

    Get-CsOnlineUser [[-Identity] <UserIdParameter>] [-Filter <String>] [-LdapFilter <String>] [-OnOfficeCommunicationServer] [-OnLyncServer] [-UnAssignedUser] [-OU <OUIdParameter>] [-DomainController <Fqdn>] [-Credential <PSCredential>] [-ResultSize <Unlimited`1>] [-Verbose]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 returns information for all the users configured as online users.

    Get-CsOnlineUser

</div>

<div>

## Example 2

In Example 2 information is returned for a single online user: the user with the SIP address "sip:kenmyer@litwareinc.com".

    Get-CsOnlineUser -Identity "sip:kenmyer@litwareinc.com"

</div>

<div>

## Example 3

The command shown in Example 3 returns information for all the online users who have been enabled for Lync Online but are not currently assigned to a Registrar pool.

    Get-CsOnlineUser -UnassignedUser

</div>

<div>

## Example 4

Example 4 uses the Filter parameter to limit the returned data to online users who have been assigned the per-user archiving policy RedmondArchiving. To do this, the filter value {ArchivingPolicy -eq "RedmondArchiving"} is employed; that syntax limits returned data to users where the ArchivingPolicy property is equal to (-eq) "RedmondArchiving".

    Get-CsOnlineUser -Filter {ArchivingPolicy -eq "RedmondArchiving"}

</div>

<div>

## Example 5

Example 5 returns information only for user accounts that have been configured so that the account does not appear in Microsoft Exchange address lists. (That is, the Active Directory attribute msExchHideFromAddressLists is True.) To carry out this task, the Filter parameter is included along with the filter value {HideFromAddressLists -eq $True}.

    Get-CsOnlineUser -Filter {HideFromAddressLists -eq $True}

</div>

<div>

## Example 6

The command shown in Example 6 returns information for all the online users assigned to the tenant with the TenantID "bf19b7db-6960-41e5-a139-2aa373474354". To accomplish the task, the command includes the Filter parameter along with the filter value {TenantId –eq "bf19b7db-6960-41e5-a139-2aa373474354"}. This filter limits the returned data to online users assigned to the tenant "bf19b7db-6960-41e5-a139-2aa373474354".

    Get-CsOnlineUser -Filter {TenantId -eq "bf19b7db-6960-41e5-a139-2aa373474354"}

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The **Get-CsOnlineUser** cmdlet returns information about users who have accounts homed on Microsoft Lync Online. The returned information includes standard Active Directory account information (such as the department the user works in, his or her address and phone number, etc.) as well as Lync Server specific information: the **Get-CsOnlineUser** cmdlet returns information about such things as whether or not the user has been enabled for Enterprise Voice and which per-user policies (if any) have been assigned to the user.

Note that the **Get-CsOnlineUser** cmdlet does not have a TenantId parameter; that means you cannot use a command similar to this in order to limit the returned data to users who have accounts with a specific Lync Online tenant:

    Get-CsOnlineUser -TenantId "bf19b7db-6960-41e5-a139-2aa373474354"

However, if you have multiple Lync Online tenants you can return users from a specified tenant by using the Filter parameter and a command similar to this:

    Get-CsOnlineUser -Filter {TenantId -eq "bf19b7db-6960-41e5-a139-2aa373474354"}

That command will limit the returned data to user accounts belong to the tenant with the TenantId "bf19b7db-6960-41e5-a139-2aa373474354". If you do not know your tenant IDs you can return that information by using this command:

    Get-CsTenant

If you have a hybrid or "split domain" deployment (that is, a deployment in which some users have accounts homed on Lync Online while other users have accounts homed on an on-premises version of Lync Server) keep in mind that the **Get-CsOnlineUser** cmdlet only returns information for Lync Online users. However, the [Get-CsUser](get-csuser.md) cmdlet will return information for both Lync Online users and on-premises Lync Server users. If you want to exclude Lync Online users from the data returned by the **Get-CsUser** cmdlet, use the following command:

    Get-CsUser -Filter {TenantId -eq "00000000-0000-0000-0000-000000000000"}

By definition, users homed on the on-premises version of Lync Server will always have a TenantId equal to 00000000-0000-0000-0000-000000000000. Users homed on Lync Online will a TenantId that is equal to some value other than 00000000-0000-0000-0000-000000000000.

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
<td><p><em>Credential</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.PSCredential</p></td>
<td><p>Enables you to run the <strong>Get-CsOnlineUser</strong> cmdlet under alternate credentials. This might be required if the account you used to log on to the Windows does not have the necessary privileges required to work with user objects.</p>
<p>To use the Credential parameter you must first create a PSCredential object by using the <strong>Get-Credential</strong> cmdlet. For details, see the <strong>Get-Credential</strong> cmdlet help topic.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Enables you to connect to the specified domain controller in order to retrieve user information. To connect to a particular domain controller, include the DomainController parameter followed by the fully qualified domain name (FQDN) (for example, atl-cs-001.litwareinc.com).</p></td>
</tr>
<tr class="odd">
<td><p><em>Filter</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to limit the returned data by filtering on Lync Server specific attributes. For example, you can limit returned data to users who have been assigned a specific voice policy, or users who have not been assigned a specific voice policy.</p>
<p>The Filter parameter uses the same Windows PowerShell filtering syntax that is used by the Where-Object cmdlet. For example, a filter that returns only users who have been enabled for Enterprise Voice would look like this, with EnterpriseVoiceEnabled representing the Active Directory attribute, -eq representing the comparison operator (equal to), and $True (a built-in Windows PowerShell variable) representing the filter value:</p>
<p>{EnterpriseVoiceEnabled -eq $True}</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>Indicates the Identity of the user account to be retrieved. User Identities can be specified using one of four formats: 1) the user's SIP address; 2) the user's user principal name (UPN); 3) the user's domain name and logon name, in the form domain\logon (for example, litwareinc\kenmyer); and, 4) the user's Active Directory display name (for example, Ken Myer). You can also reference a user account by using the user’s Active Directory distinguished name.</p>
<p>You can use the asterisk (*) wildcard character when using the Display Name as the user Identity. For example, the Identity &quot;* Smith&quot; returns all the users who have a display name that ends with the string value &quot; Smith&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><em>LdapFilter</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to limit the returned data by filtering on generic Active Directory attributes (that is, attributes that are not specific to Lync Server). For example, you can limit returned data to users who work in a specific department, or users who have a specified manager or job title.</p>
<p>The LdapFilter parameter uses the LDAP query language when creating filters. For example, a filter that returns only users who work in the city of Redmond would look like this: &quot;l=Redmond&quot;, with &quot;l&quot; (a lowercase L) representing the Active Directory attribute (locality); &quot;=&quot; representing the comparison operator (equal to); and &quot;Redmond&quot; representing the filter value.</p></td>
</tr>
<tr class="even">
<td><p><em>OnLyncServer</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Returns a collection of users homed on Lync Server. Users with accounts on previous versions of the software will not be returned when you use this parameter.</p></td>
</tr>
<tr class="odd">
<td><p><em>OnOfficeCommunicationServer</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Returns a collection of users homed on a previous version of Lync Server (for example, Microsoft Office Communications Server 2007 R2). Users with accounts on the current version of the software will not be returned when you use this parameter.</p></td>
</tr>
<tr class="even">
<td><p><em>OU</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.AD.OUIdParameter</p></td>
<td><p>Enables you to return information about user accounts in a specific organizational unit (OU) or container. The OU parameter returns data from both the specified OU and any of its child OUs. For example, if the Finance OU has two child OUs -- AccountsPayable and AccountsReceivable -- users will be returned from each of these three OUs.</p>
<p>When specifying an OU, use the distinguished name (DN) of that container; for example: -OU &quot;OU=Finance,dc=litwareinc,dc=com&quot;. To return user accounts from the Users container, use this syntax:</p>
<p>-OU &quot;cn=Users,dc=litwareinc,dc=com&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>ResultSize</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.Unlimited</p></td>
<td><p>Enables you to limit the number of records returned by the cmdlet. For example, to return seven users (regardless of the number of users that are in your forest) include the ResultSize parameter and set the parameter value to 7. Note that there is no way to guarantee which seven users will be returned.</p>
<p>The result size can be set to any whole number between 0 and 2147483647, inclusive. If set to 0 the command will run, but no data will be returned. If you set the ResultSize to 7 but you have only three users in your forest, the command will return those three users, and then complete without error.</p></td>
</tr>
<tr class="even">
<td><p><em>UnassignedUser</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Enables you to return a collection of all the users who have been enabled for Lync Online but are not currently assigned to a Registrar pool. Users are not allowed to log on to unless they are assigned to a Registrar pool.</p></td>
</tr>
</tbody>
</table>


</div>

<span id="InputTypes"></span>

<div>

## Input Types

The **Get-CsOnlineUser** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADUser object, as well as string values that represent a valid user account Identity (for example, "sip:kenmyer@litwareinc.com").

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **Get-CsOnlineUser** cmdlet returns instances of the Microsoft.Rtc.Management.ADConnect.Schema.ADOCOnlineUser object.

</div>

<div>

## See Also


[Get-CsUser](get-csuser.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

