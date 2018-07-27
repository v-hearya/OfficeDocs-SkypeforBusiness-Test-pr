---
title: Managing Exchange Unified Messaging and hosted voice mail in Skype for Business Online
TOCTitle: Managing Exchange Unified Messaging and hosted voice mail
ms:assetid: 844bf8d5-e093-4dcd-abcf-48dc70e8c73c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362822(v=OCS.15)
ms:contentKeyID: 56558820
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Managing Exchange Unified Messaging and hosted voice mail in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2015-03-09_

The following cmdlets can be used to manage Exchange Unified Messaging (UM) and hosted voice mail policies:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Cmdlet</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="get-csexumcontact.md">Get-CsExUmContact</a></p>
<p><a href="new-csexumcontact.md">New-CsExUmContact</a></p>
<p><a href="remove-csexumcontact.md">Remove-CsExUmContact</a></p>
<p><a href="set-csexumcontact.md">Set-CsExUmContact</a></p></td>
<td><p>Creates and manages contact objects used for Auto Attendant and Subscriber Access services, when Exchange UM is a hosted service.</p>
<p>Skype for Business Online works with Exchange UM to provide several voice-related capabilities, including Auto Attendant and Subscriber Access. Auto Attendant provides a way for calls to automatically be answered and routed to the correct person. Subscriber Access enables users to connect to Exchange UM and retrieve email, voice messages, contacts, and calendar information.</p>
<p>When Exchange UM is provided as a hosted service, contact objects used for the Auto Attendant and Subscriber Access services must be created by using Windows PowerShell. These objects are created and managed by using the CsExUmContact cmdlets.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-cshostedvoicemailpolicy.md">Get-CsHostedVoicemailPolicy</a></p>
<p><a href="grant-cshostedvoicemailpolicy.md">Grant-CsHostedVoicemailPolicy</a></p></td>
<td><p>Manages hosted voicemail policies used in the organization. Hosted voicemail policies specify how unanswered calls are routed to the Exchange UM service. These policies affect only users who have been enabled for Exchange UM hosted voicemail. To verify whether a user is enabled for hosted voicemail, run a command similar to this from the Windows PowerShell prompt:</p>
<pre><code>Get-CsOnlineUser -Identity &quot;kenmyer@litwareinc.com&quot; | Select-Object HostedVoiceMail</code></pre></td>
</tr>
</tbody>
</table>


You cannot manage Exchange UM settings and hosted voicemail policies by using the Skype for Business Online admin center.

<div>

## See Also


[The Skype for Business Online cmdlets](the-skype-for-business-online-cmdlets.md)  
[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

