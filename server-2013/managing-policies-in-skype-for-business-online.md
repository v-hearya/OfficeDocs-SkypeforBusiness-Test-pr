---
title: Managing policies in Skype for Business Online
TOCTitle: Managing policies
ms:assetid: 91372888-a96e-44db-a0dc-d08facbfce87
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362826(v=OCS.15)
ms:contentKeyID: 56558837
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Managing policies in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2015-03-09_

The following cmdlets manage Skype for Business Online policies. Policies help determine the Skype for Business Online capabilities that are available to users and to the organization as a whole.


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
<td><p><a href="get-csclientpolicy.md">Get-CsClientPolicy</a><br />
<a href="grant-csclientpolicy.md">Grant-CsClientPolicy</a></p></td>
<td><p>Client policies are used to determine the Lync client features that are available to users. For example, you might give the capability to transfer files to some users, but not to others.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-csconferencingpolicy.md">Get-CsConferencingPolicy</a><br />
<a href="grant-csconferencingpolicy.md">Grant-CsConferencingPolicy</a></p></td>
<td><p>Conferencing policies determine the features and capabilities that can be used in a conference. This includes everything from whether the conference can include IP audio and video to the maximum number of people who can attend a meeting.</p></td>
</tr>
<tr class="odd">
<td><p><a href="get-csexternalaccesspolicy.md">Get-CsExternalAccessPolicy</a><br />
<a href="grant-csexternalaccesspolicy.md">Grant-CsExternalAccessPolicy</a></p></td>
<td><p>External access policies are used to determine whether your users are allowed to communicate with users from federated domains, and/or whether your users are allowed to communicate with users who have accounts on public IM providers, such as Windows Live or AOL.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-csvoicepolicy.md">Get-CsVoicePolicy</a><br />
<a href="grant-csvoicepolicy.md">Grant-CsVoicePolicy</a><br />
<a href="remove-csvoicepolicy.md">Remove-CsVoicePolicy</a></p></td>
<td><p>Voice policies are used to manage Enterprise Voice features, as simultaneous ringing (the ability to have a second phone ring each time someone calls your office phone) and call forwarding.</p></td>
</tr>
</tbody>
</table>


You can also manage selected conferencing policy settings by using the Skype for Business Online admin center:

![Lync admin center general options properties](images/Dn362833.acf90793-7ee4-4faf-b791-f149dd5df2a5(OCS.15).png "Lync admin center general options properties")

You can also manage external access policy settings by using the Skype for Business Online admin center:

![Admin center external communication options](images/Dn362826.e5cfb159-b096-463e-b1ef-2b42eb29168a(OCS.15).png "Admin center external communication options")

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

