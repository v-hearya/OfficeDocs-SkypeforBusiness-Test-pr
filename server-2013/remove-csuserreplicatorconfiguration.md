---
title: Remove-CsUserReplicatorConfiguration
TOCTitle: Remove-CsUserReplicatorConfiguration
ms:assetid: 26c3a357-558f-406f-8df3-059911f771f0
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425738(v=OCS.15)
ms:contentKeyID: 48183658
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsUserReplicatorConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Removes the specified collection of User Replicator configuration settings. The User Replicator periodically retrieves up-to-date user account information from Active Directory and then synchronizes the new information with the current user data stored by Lync Server. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsUserReplicatorConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 resets the global User Replicator configuration settings.

    Remove-CsUserReplicatorConfiguration -Identity global

</div>

</div>

<div>

## Detailed Description

Although Lync Server maintains its own database of user accounts and user account data, Lync Server still relies on Active Directory as the ultimate source for user information. For example, when a new Active Directory user account is created, you must supply basic information about the user account (such as the Active Directory display name). However, when a user is enabled for Lync Server you do not need to specify a new display name. That’s because Lync Server uses the display name already stored in Active Directory.

Of course, user account information, including the Active Directory display name, is subject to change over time. For example, a user who gets married might change her last name and, in turn, need to change her display name as well. In order to ensure that the Lync Server database and Active Directory remain in synch, Lync Server must periodically connect to Active Directory, retrieve the latest user account updates, and then modify the Lync Server user database accordingly. This synchronization between Active Directory and Lync Server is carried out by the User Replicator.

When you install Lync Server a global set of User Replicator configuration settings is created for you. By default, these settings are used to manage the User Replicator on an organization-wide basis. Management of the User Replicator consists of identifying the domains that Lync Server needs to synch with and indicating how often the User Replicator checks Active Directory for user account updates. By default, the User Replicator discovers and synchs with all available domains. However, by using the AdDomainNamingContextList property you can restrict synchronization to a specific set of domains: the domains that appear in the AdDomainNamingContextList property.

You can also create additional collections at the service scope, but only if you are working with Lync Online.

If your needs change, you can use the **Remove-CsUserReplicatorConfiguration** cmdlet to remove the custom settings created at the service scope. Note that you can also run this cmdlet against the global configuration settings. In that case, however, the global settings will not be removed. Instead, all the properties within the global collection will be reset to their default values. In the case of the User Replicator, that means erasing the list of domains that must be synchronized with (thus causing the replicator to synch with all discoverable domains), and setting the replication interval cycle to 1 minute.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsUserReplicatorConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself) run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsUserReplicatorConfiguration"}

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
<td><p>Unique identifier of the User Replicator configuration settings to be removed. To remove settings at the service scope, use syntax similar to this: -Identity &quot;service:Registrar:atl-cs-001.litwareinc.com&quot;. (Note that you can only remove service-scoped setting if you are using Lync Online). To reset the global settings, use this syntax: -Identity global. You cannot use wildcards when specifying an Identity.</p></td>
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
<td><p>Suppresses the display of any non-fatal error message that might arise when running the command.</p></td>
</tr>
<tr class="even">
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

Microsoft.Rtc.Management.WritableConfig.Settings.UserReplicator.UserReplicatorConfiguration object. The **Remove-CsUserReplicatorConfiguration** cmdlet accepts pipelined input of the User Replicator configuration object.

</div>

<div>

## Return Types

None. Instead, the **Remove-CsUserReplicatorConfiguration** cmdlet deletes instances of the Microsoft.Rtc.Management.WritableConfig.Settings.UserReplicator.UserReplicatorConfiguration object.

</div>

<div>

## See Also


[Get-CsUserReplicatorConfiguration](get-csuserreplicatorconfiguration.md)  
[New-CsUserReplicatorConfiguration](new-csuserreplicatorconfiguration.md)  
[Set-CsUserReplicatorConfiguration](set-csuserreplicatorconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

