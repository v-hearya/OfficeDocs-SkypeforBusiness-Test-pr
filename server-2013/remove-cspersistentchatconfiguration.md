---
title: Remove-CsPersistentChatConfiguration
TOCTitle: Remove-CsPersistentChatConfiguration
ms:assetid: 5b71b66b-9b9b-4833-94b8-528260cd7589
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204927(v=OCS.15)
ms:contentKeyID: 48184241
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsPersistentChatConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-07_

Removes an existing collection of Persistent Chat configuration settings. Persistent Chat configuration settings are used to manage the Persistent Chat service. For example, these settings allow you to specify the maximum number of users who can participate in a chat room. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Remove-CsPersistentChatConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 deletes the Persistent Chat configuration settings for the Redmond site.

    Remove-CsPersistentChatConfiguration -Identity "site:Redmond"

</div>

<div>

## Example 2

In Example 2, all the Persistent Chat configuration settings applied to the site scope are removed. To do this, the command first employs the **Get-CsPersistentChatConfiguration** cmdlet and the –Filter parameter; the filter value "site:\*" limits the returned data to settings applied at the site scope. These settings are then piped to the **Remove-CsPersistentChatConfiguration** cmdlet, which deletes all the settings applied to the site scope.

    Get-CsPersistentChatConfiguration -Filter "site:*" | Remove-CsPersistentChatConfiguration

</div>

<div>

## Example 3

Example 3 deletes all the Persistent Chat configuration settings where the default chat history is greater than 30. To carry out this task the command first uses the **Get-CsPersistentChatConfiguration** cmdlet to return a collection of all the Persistent Chat configuration settings. This collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the DefaultChatHistory property is greater than (-gt) 30. The filtered collection is then piped to the **Remove-CsPersistentChatConfiguration** cmdlet, which deletes each item in the filtered collection.

    Get-CsPersistentChatConfiguration | Where-Object {$_.DefaultChatHistory -gt 30} | Remove-CsPersistentChatConfiguration

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.

The Persistent Chat service is managed, in part, by Persistent Chat configuration settings, which dictate such things as the number of previously-posted chat messages immediately available when you log on to a chat room (the chat history) or the maximum size of a file that can be uploaded to (or downloaded from) the service. These settings can be configured at the global or the site scope, or at the service scope (that is, you can have a custom collection of settings assigned to an individual Persistent Chat pool).

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsPersistentChatConfiguration"}

**Lync Server Control Panel:** To remove a collection of Persistent Chat configuration settings using the Lync Server Control Panel, click **Persistent Chat** and then click **Persistent Chat Configuration**. Select the collection to be removed, click **Edit**, and then click **Delete**.

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
<td><p>Unique identifier for the Persistent Chat configuration settings to be removed. To remove a collection of settings configured at the site scope, use syntax similar to this:</p>
<p>-Identity &quot;site:Redmond&quot;</p>
<p>To remove a collection configured at the service scope, use syntax like this:</p>
<p>-Identity &quot;service:PersistentChatServer:atl-gc-001.litwareinc.com&quot;</p>
<p>Note that you cannot use wildcards with the Identity parameter.</p>
<p>You can also run the <strong>Remove-CsPersistentChatConfiguration</strong> against cmdlet the global settings collection. In that case, however, the global collection will not be removed. Instead, all the properties within that collection will be reset to their default values.</p></td>
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
<td><p><em>WhatIf</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Describes what would happen if you executed the command without actually executing the command.</p></td>
</tr>
</tbody>
</table>


</div>

<span id="InputTypes"></span>

<div>

## Input Types

The **Remove-CsPersistentChatConfiguration** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatConfiguration object.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

None. Instead, the **Remove-CsPersistentChatConfiguration** cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.PersistentChat.PersistentChatConfiguration object.

</div>

<div>

## See Also


[Get-CsPersistentChatConfiguration](get-cspersistentchatconfiguration.md)  
[New-CsPersistentChatConfiguration](new-cspersistentchatconfiguration.md)  
[Set-CsPersistentChatConfiguration](set-cspersistentchatconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

