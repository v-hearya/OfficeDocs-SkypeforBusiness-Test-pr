---
title: Get-CsCommonAreaPhone
TOCTitle: Get-CsCommonAreaPhone
ms:assetid: bfb7927b-49a7-4637-a9ff-fd68897efb45
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412934(v=OCS.15)
ms:contentKeyID: 48185297
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsCommonAreaPhone

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Returns information about the common area phones managed by using Lync Server. Common area phones are phones that are located in building lobbies, employee lounges, or other areas where they are likely to be used by a number of different people and for a number of different uses. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsCommonAreaPhone [-Identity <UserIdParameter>] [-Credential <PSCredential>] [-DomainController <Fqdn>] [-Filter <String>] [-LdapFilter <String>] [-OU <OUIdParameter>] [-ResultSize <Unlimited>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 returns information about all the common area phones configured for use in the organization. This is done by calling the **Get-CsCommonAreaPhone** cmdlet without any parameters.

    Get-CsCommonAreaPhone

</div>

<div>

## EXAMPLE 2

In Example 2, the common area phone with the Active Directory display name "Building 14 Lobby" is returned. This task is carried out by including the Filter parameter and the filter value {DisplayName -eq "Building 14 Lobby"}; that filter value limits returned objects to common area phones where the DisplayName property is equal to "Building 14 Lobby".

    Get-CsCommonAreaPhone -Filter {DisplayName -eq "Building 14 Lobby"}

</div>

<div>

## EXAMPLE 3

Example 3 returns all the common area phones that have an Active Directory display name that begins with the characters "Building 14". To do this, the **Get-CsCommonAreaPhone** cmdlet is called, along with the Filter parameter and the filter value {DisplayName -like "Building 14\*"}. The filter value uses the -like operator and the wildcard string "Building 14\*" to limit returned data to phones where the DisplayName property begins with "Building 14" (for example, "Building 14 Lobby", "Building 14 Cafeteria", etc.).

    Get-CsCommonAreaPhone  -Filter {DisplayName -like "Building 14*"}

</div>

<div>

## EXAMPLE 4

In Example 4, a single common area phone is returned: the phone that has a LineUri property equal to "tel:+14255551234". Because LineUris must be unique, this command will never return more than a single item.

    Get-CsCommonAreaPhone  -Filter {LineUri -eq "tel:+14255551234"}

</div>

<div>

## EXAMPLE 5

The command shown in Example 5 returns information about all the common area phones that have not been assigned a dial plan. This is done by using the Filter parameter and the filter value {DialPlan -eq $Null}; that limits returned data to phones where the DialPlan property is equal to a null value. If a common area phone has not explicitly been assigned a dial plan, then it automatically uses the global dial plan or, if one exists, the dial plan assigned to the site.

    Get-CsCommonAreaPhone -Filter {DialPlan -eq $Null}

</div>

<div>

## EXAMPLE 6

Example 6 returns a collection of all the common area phones that have a contact object in the Telecommunications OU in Active Directory Domain Services. To do this, the **Get-CsCommonAreaPhone** cmdlet is called along with the OU parameter; the parameter value limits the returned objects to phones that have contacts objects in the OU with the distinguished name ou=Telecommunications,dc=litwareinc,dc=com.

    Get-CsCommonAreaPhone -OU "ou=Telecommunications,dc=litwareinc,dc=com"

</div>

</div>

<div>

## Detailed Description

Common area phones are IP telephones that are not associated with an individual user. Instead of being located in someone’s office, common area phones are typically located in building lobbies, cafeterias, employee lounges, meeting rooms and other locations where a large number of people are likely to gather. This presents administrators with a management challenge; that’s because phone use in Lync Server is typically maintained by using voice policies and dial plans that are assigned to individual users. Common area phones do not have individual users assigned to them.

The solution to this challenge is to create Active Directory contact objects for all your common area phones. (These contact objects can be created by using the **New-CsCommonAreaPhone** cmdlet.) Like user accounts, these contact objects can be assigned policies and voice plans. As a result, you will be able to maintain control over common area phones even though those phones are not associated with an individual user. For example, if you do not want people to have the ability to transfer or park calls from a common area phone, you can create a voice policy that prohibits call transfers and call parking, and then assign that policy to the common area phone. (Or, more correctly, to the contact object that represents the common area phone.) For example, this command assigns the voice policy CommonAreaPhoneVoicePolicy to all your common area phones:

Get-CsCommonAreaPhone | Grant-CsVoicePolicy –PolicyName "CommonAreaPhoneVoicePolicy"

The **Get-CsCommonAreaPhone** cmdlet provides a way for you to retrieve information about the common area phones configured for use in your organization. If you call the **Get-CsCommonAreaPhone** cmdlet without any parameters, the cmdlet will return information about all your common area phones. Optional parameters provide different ways for you to filter information; for example, you can return all the common area phones that have contact objects in a specified organizational unit (OU), or all the contacts objects located in a specified building.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsCommonAreaPhone** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins, RTCUniversalReadOnlyAdmins. Permissions to run this cmdlet for specific sites or specific Active Directory OUs can be assigned by using the **Grant-CsOUPermission** cmdlet. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsCommonAreaPhone"}

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
<td><p>Enables you to run the <strong>Get-CsCommonAreaPhone</strong> cmdlet under alternate credentials. This might be required if the account you used to log on to Windows does not have the necessary privileges required to work with contact objects.</p>
<p>To use the Credential parameter, you must first create a PSCredential object by using the <strong>Get-Credential</strong> cmdlet. For details, see the <strong>Get-Credential</strong> cmdlet help topic.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Enables you to connect to the specified domain controller in order to retrieve contact information. To connect to a particular domain controller, include the DomainController parameter followed by the fully qualified domain name (FQDN) of that computer (for example, atl-cs-001.litwareinc.com).</p></td>
</tr>
<tr class="odd">
<td><p><em>Filter</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to limit the returned data by filtering on attributes specific to Lync Server. For example, you can limit returned data to common area phone contact objects that have been assigned a specific voice policy, or contacts that have not been assigned a specific voice policy.</p>
<p>The Filter parameter uses the same Windows PowerShell filtering syntax that is used by the <strong>Where-Object</strong> cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>Unique identifier for the common area phone. Common area phones are identified using the Active Directory distinguished name (DN) of the associated contact object. By default, common area phones use a globally unique identifier (GUID) as their common name, which means phones will typically have an Identity similar to this: CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com.</p></td>
</tr>
<tr class="odd">
<td><p><em>LdapFilter</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to limit the returned data by filtering on generic Active Directory attributes (that is, attributes that are not specific to Lync Server). For example, you can limit returned data to contact objects that have been assigned to a specific department or are located in a specific building.</p>
<p>The LdapFilter parameter uses the LDAP query language when creating filters. For example, a filter that returns only contact objects representing common area phones in the city of Redmond would look like this:</p>
<p>-LDAPFilter &quot;l=Redmond&quot;</p>
<p>In the preceding filter, &quot;l&quot; (a lowercase L) represents the Active Directory attribute (locality); &quot;=&quot; represents the comparison operator (equal to); and &quot;Redmond&quot; represents the filter value.</p></td>
</tr>
<tr class="even">
<td><p><em>OU</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.AD.OUIdParameter</p></td>
<td><p>Enables you to return contact objects from a specific Active Directory organizational unit (OU). The OU parameter returns data from both the specified OU and any of its child OUs. For example, if the Finance OU has two child OUs -- AccountsPayable and AccountsReceivable -- common area phone information will be returned from each of these OUs.</p>
<p>When specifying an OU, use the distinguished name of that container; for example: -OU &quot;OU=Finance,dc=litwareinc,dc=com&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><em>ResultSize</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.Unlimited</p></td>
<td><p>Enables you to limit the number of records returned by a command. For example, to return seven common area phones (regardless of how many common area phones are in your forest) include the ResultSize parameter and set the parameter value to 7. Note that there is no way to guarantee which seven phones will be returned. If you set the ResultSize to 7 but you have only three common area phones in your forest, the command will return those three phones, and then complete without error.</p>
<p>The result size can be set to any whole number between 0 and 2147483647, inclusive. If set to 0 the command will run, but no data will be returned.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

String. The **Get-CsCommonAreaPhone** cmdlet accepts a pipelined string value that represents the Identity of the common area phone.

</div>

<div>

## Return Types

The **Get-CsCommonAreaPhone** cmdlet returns instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADCommonAreaPhoneContact object.

</div>

<div>

## See Also


[Move-CsCommonAreaPhone](move-cscommonareaphone.md)  
[New-CsCommonAreaPhone](new-cscommonareaphone.md)  
[Remove-CsCommonAreaPhone](remove-cscommonareaphone.md)  
[Set-CsCommonAreaPhone](set-cscommonareaphone.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

