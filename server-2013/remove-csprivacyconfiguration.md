---
title: Remove-CsPrivacyConfiguration
TOCTitle: Remove-CsPrivacyConfiguration
ms:assetid: 32052c51-953d-4278-9425-306245d297ed
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425821(v=OCS.15)
ms:contentKeyID: 48183809
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsPrivacyConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-07_

Removes an existing collection of privacy configuration settings. Privacy configuration settings help determine how much information users make available to other users. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsPrivacyConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 returns the privacy configuration settings assigned to the Redmond site. When these settings are deleted, users in the Redmond site will automatically inherit the global privacy configuration settings.

    Remove-CsPrivacyConfiguration -Identity site:Redmond

</div>

<div>

## EXAMPLE 2

In Example 2, all the privacy configuration settings assigned at the site scope are deleted, To do this, the command first calls the **Get-CsPrivacyConfiguration** cmdlet along with the Filter parameter; the filter value "site:\*" ensures that only those settings that have an Identity that begins with the characters "site" are returned. The filtered collection is then piped to the **Remove-CsPrivacyConfiguration** cmdlet, which removes each item in the collection.

    Get-CsPrivacyConfiguration -Filter "site:*" | Remove-CsPrivacyConfiguration

</div>

<div>

## EXAMPLE 3

The command shown in Example 3 deletes all the privacy configuration settings where privacy mode has been disabled. To carry out this task, the command first calls the **Get-CsPrivacyConfiguration** cmdlet without any parameters; that returns a collection of all the privacy configuration settings in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which selects only those settings where the EnablePrivacyMode property is equal to False. This filtered collection is piped to the **Remove-CsPrivacyConfiguration** cmdlet, which deletes each item in the collection.

    Get-CsPrivacyConfiguration | Where-Object {$_.EnablePrivacyMode -eq $False} | Remove-CsPrivacyConfiguration

</div>

</div>

<div>

## Detailed Description

Lync Server gives users the opportunity to share a wealth of presence information with other people: they can publish a photograph of themselves; they can provide detailed location information; they can have presence information automatically made available to everyone in the organization (as opposed to having this information available only to people on their Contacts list).

Some users will welcome the opportunity to make this information available to their colleagues; other users might be more reluctant to share this data. (For example, many people might be hesitant about having their photo included in their presence data.) As a general rule, users have control over what information they will (or will not) share; for example, users can select or clear a check box in order to control whether or not their location information is shared with others. In addition, the privacy configuration cmdlets enable administrators to manage privacy settings for their users. In some cases, administrators can enable or disable settings. For example, if the property AutoInitiateContacts is set to True, then team members will automatically be added to each user’s Contacts list; if set to False, team members will not be automatically be added to each user’s Contacts list.

In other cases, administrators can configure the default values in Lync Server while still giving users the right to change these values. For example, by default location data is published for users, although users do have the right to stop location publication. By setting the PublishLocationDataByDefault property to False, administrators can change this behavior: in that case, location data will not be published by default, although users will still have the right to publish this data if they choose.

Privacy configuration settings can be applied at the global scope, the site scope, and at the service scope (albeit only for the User Server service). The **Remove-CsPrivacyConfiguration** cmdlet provides a way for you to delete settings that have been configured at either the site or service scope; for example, if you run the cmdlet against settings configured at the site scope, those settings will be deleted and users in that site will have their privacy settings governed by the global collection. The **Remove-CsPrivacyConfiguration** cmdlet can also be run against the global collection; however, the global collection will not be deleted. Instead, all that properties in that collection will be reset to their default values. For example, suppose you previously changed the EnablePrivacyMode property to True. If you now "delete" the global collection EnablePrivacyMode will revert to its default value of False.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsPrivacyConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself) run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsPrivacyConfiguration"}

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
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Unique identifier for the privacy configuration settings to be removed. To remove settings configured at the site scope, use syntax similar to this: -Identity site:Redmond. To remove settings at the service level, use syntax like this: -Identity service:UserServer:atl-cs-001.litwareinc.com.</p>
<p>The <strong>Remove-CsPrivacyConfiguration</strong> cmdlet can also be run against the global collection of settings. In that case, however, the global settings will not be deleted. Instead, all the properties in that collection will be reset to their default values.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Guid</p></td>
<td><p>Globally unique identifier (GUID) of the Lync Online tenant account for which privacy configuration settings being deleted. For example:</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>You can return the tenant ID for each of your tenants by running this command:</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Describes what would happen if you executed the command without actually executing the command.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PrivacyConfiguration object. The **Remove-CsPrivacyConfiguration** cmdlet accepts pipelined input of the privacy configuration object.

</div>

<div>

## Return Types

None. Instead, the **Remove-CsPrivacyConfiguration** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PrivacyConfiguration object.

</div>

<div>

## See Also


[Get-CsPrivacyConfiguration](get-csprivacyconfiguration.md)  
[New-CsPrivacyConfiguration](new-csprivacyconfiguration.md)  
[Set-CsPrivacyConfiguration](set-csprivacyconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

