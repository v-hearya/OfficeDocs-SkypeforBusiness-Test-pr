---
title: Get-CsAddressBookConfiguration
TOCTitle: Get-CsAddressBookConfiguration
ms:assetid: 07757a19-f819-4d65-82da-50bf2f157a9b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398132(v=OCS.15)
ms:contentKeyID: 48183317
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsAddressBookConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-20_

Returns information about Address Book configuration settings. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsAddressBookConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsAddressBookConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 returns information about all the Address Book configuration settings in use in your organization. This is the default behavior if you call the **Get-CsAddressBookConfiguration** cmdlet without any additional parameters.

    Get-CsAddressBookConfiguration

</div>

<div>

## EXAMPLE 2

Example 2 returns information for the Address Book configuration settings with the Identity site:Redmond.

    Get-CsAddressBookConfiguration -Identity site:Redmond

</div>

<div>

## EXAMPLE 3

In this example, the Filter parameter and the filter value "site:\*" are used to return information about all the Address Book configuration settings that have been applied at the site scope. The supplied filter value returns information for all the Address Book settings that have an Identity that begins with the string value "site:".

    Get-CsAddressBookConfiguration -Filter site:*

</div>

<div>

## EXAMPLE 4

In Example 4, information is returned for all the Address Book configuration settings where the settings uses normalization rules when parsing phone numbers. To do this, the command first uses the **Get-CsAddressBookConfiguration** cmdlet to return a collection of all the Address Book settings in the organization. That collection is then piped to the **Where-Object** cmdlet, which selects only those settings where the UseNormalizationRules property is equal to True.

    Get-CsAddressBookConfiguration | Where-Object {$_.UseNormalizationRules -eq $True}

</div>

</div>

<div>

## Detailed Description

Address Book servers are intermediaries between Active Directory Domain Services and Lync Server. The Address Book server ensures that the user information stored in Lync Server is in synch with the user information stored in Active Directory. This is done by periodically synching Address Book files with information stored in the User database.

In addition, Address Book servers periodically generate index files that are downloaded to computers running Lync. When a user searches for contacts, he or she either search through these index files or search the Address Book index files stored in the Central Management store.

Address Book servers are governed using Address Book configuration settings; these settings determine such things as how often Address Book files are synchronized with the user database and how often these Address Book index files are generated. When you install Lync Server, a set of global Address Book settings is created for you. You can also create custom configuration settings that can be applied to individual sites. These settings, if they exist, apply to any Address Book servers operating in the site, and take precedence over the global settings.

You can use the **Get-CsAddressBookConfiguration** cmdlet to return information about any (or all) of the Address Book settings currently in use in your organization.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsAddressBookConfiguration** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsAddressBookConfiguration"}

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
<td><p><em>Filter</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to use wildcard characters in order to return a collection (or multiple collections) of Address Book settings. For example, to return a collection of all the settings configured at the site scope, use this syntax: -Filter site:*. To return a collection of all the settings that have the string value &quot;EMEA&quot; somewhere in their Identity, use this syntax: -Filter *EMEA*.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Unique identifier for the collection of Address Book settings to be returned. To refer to the global settings, use this syntax: -Identity global. To refer to a collection configured at the site scope, use syntax similar to this: -Identity site:Redmond.</p>
<p>Note that you cannot use wildcards when specifying an Identity. If you need to use wildcards, then include the Filter parameter instead.</p>
<p>If this parameter is not specified, then the <strong>Get-CsAddressBookConfiguration</strong> cmdlet returns a collection of all the Address Book settings in use in the organization.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the Address Book configuration data from the local replica of the Central Management store rather than from the Central Management store itself.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Get-CsAddressBookConfiguration** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Get-CsAddressBookConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.AddressBook.AddressBookSettings object.

</div>

<div>

## See Also


[New-CsAddressBookConfiguration](new-csaddressbookconfiguration.md)  
[Remove-CsAddressBookConfiguration](remove-csaddressbookconfiguration.md)  
[Set-CsAddressBookConfiguration](set-csaddressbookconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

