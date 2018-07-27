---
title: New-CsPersistentChatAddin
TOCTitle: New-CsPersistentChatAddin
ms:assetid: 0566f4c2-0903-4dd1-87bc-784f0bdb4391
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204641(v=OCS.15)
ms:contentKeyID: 48183286
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsPersistentChatAddin

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Enables you to configure a new Persistent Chat add-in. A Persistent Chat add-in is a customized web page that can be embedded within a Persistent Chat client. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    New-CsPersistentChatAddin -Name <String> -Url <String> [-PersistentChatPoolFqdn <String>]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 creates a new Persistent Chat add-in (with the name ITPersistentChatAddin) for the pool atl-cs-001.litwareinc.com. The URL parameter and the parameter value http://atl-cs-001.litwareinc.com/itchat specify the location of the add-in's webpage.

    New-CsPersistentChatAddin -Name "ITPersistentChatAddin" -PersistentChatPoolFqdn "atl-cs-001.litwareinc.com" -Url "http://atl-cs-001.litwareinc.com/itchat"

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The Persistent Chat service (which replaces the Group Chat service used in Microsoft Lync Server 2010) provides organizations with messaging and collaboration capabilities similar to those found in Internet discussion forums: users can exchange messages in real-time, yet can also revisit and restart those conversations at any time. Conversations can be based around specific topics, and these conversations can be made available to everyone or to only a selected set of users. Likewise, individual chat rooms can be configured so that anyone can post a message or configured so that only designated presenters can post messages.

Add-ins serve as extensions to a Persistent Chat chat room. Add-ins are external applications (that is, items not built into Persistent Chat itself) that are associated with a particular chat room. For example, a help desk chat room might include a URL that links to a Web page or to a Silverlight application that shows the status of the day's help requests. Lync Server Management Shell does not provide the ability to create these add-ins. Instead, the **CsPersistentChatAddin** cmdlets are used to associate (or disassociate) an add-in from a chat room.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsPersistentChatAddin"}

**Lync Server Control Panel:** To create a new Persistent Chat add-in using the Lync Server Control Panel, click **Persistent Chat**, click **Add-in**, and then click **New**.

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
<td><p><em>Name</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Friendly name to be given to the Persistent Chat add-in. Names must be unique per Persistent Chat Server pool.</p></td>
</tr>
<tr class="even">
<td><p><em>Url</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>URL of the webpage to be displayed by the Persistent Chat add-in.</p></td>
</tr>
<tr class="odd">
<td><p><em>PersistentChatPoolFqdn</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Fully qualified domain name of the Persistent Chat Server pool.</p></td>
</tr>
</tbody>
</table>


</div>

<span id="InputTypes"></span>

<div>

## Input Types

None. The **New-CsPersistentChatAddin** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **New-CsPersistentChatAddin** cmdlet creates new instances of the Microsoft.Rtc.Management.PersistentChat.Cmdlets.AddinObject object.

</div>

<div>

## See Also


[Get-CsPersistentChatAddin](get-cspersistentchataddin.md)  
[Remove-CsPersistentChatAddin](remove-cspersistentchataddin.md)  
[Set-CsPersistentChatAddin](set-cspersistentchataddin.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

