---
title: Managing the Skype for Business client from Skype for Business Online
TOCTitle: Managing the Skype for Business client
ms:assetid: d1ccc7b6-99ff-4ffd-bd29-9088fb8fe837
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362847(v=OCS.15)
ms:contentKeyID: 56558860
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Managing the Skype for Business client from Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2015-03-09_

The following cmdlets manage the Lync client:


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
<td><p><a href="get-csimfilterconfiguration.md">Get-CsImFilterConfiguration</a></p></td>
<td><p>Retrieves information about the URI restrictions in use in your organization.</p>
<p>When sending instant messages, users can embed a URI within the text of that message that refers other participants in the conversation to a particular website or share. Skype for Business Online can be configured so that hyperlinks with certain prefixes are blocked or are not active. This helps to ensure that participants can’t click the link and go to the site the URI refers to. Instead, they must copy and paste the link manually into a browser.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-cspresencepolicy.md">Get-CsPresencePolicy</a></p></td>
<td><p>Returns information about two important aspects of presence subscriptions: prompted subscribers and category subscriptions.</p>
<p>When you are added to someone’s Contact list, the default behavior is for you to receive a pop-up notification informing you that you’ve been added to that list. Until you dismiss the pop-up, each notification counts as a prompted subscriber.</p>
<p>Category subscriptions represent a request for a specific category of information—for example, an application that requests calendar data.</p></td>
</tr>
<tr class="odd">
<td><p><a href="get-csprivacyconfiguration.md">Get-CsPrivacyConfiguration</a><br />
<a href="set-csprivacyconfiguration.md">Set-CsPrivacyConfiguration</a></p></td>
<td><p>Configures default privacy values in Skype for Business Online, while still giving users the option to change these values.</p>
<p>Skype for Business Online gives users the opportunity to share a wealth of presence information with other people. Users can publish a photograph of themselves, provide detailed location information, and have presence information automatically available to everyone in the organization (instead of only to people on their Contacts list). <strong>CsPrivacyConfiguration</strong> cmdlets enable administrators to configure default privacy values in Skype for Business Online, while still allowing users the option to change these values.</p></td>
</tr>
</tbody>
</table>


You can also manage a subset of the privacy configuration settings by using the Skype for Business Online admin center:

![Lync admin center presence private mode settings](images/Dn362847.eb206b74-844d-4a7b-b1b3-0cfcb6e3614b(OCS.15).png "Lync admin center presence private mode settings")

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

