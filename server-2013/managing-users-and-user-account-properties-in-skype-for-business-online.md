---
title: Managing users and user account properties in Skype for Business Online
TOCTitle: Managing users and user account properties
ms:assetid: 5d13ab15-0e12-4bd0-a970-f130de980404
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362790(v=OCS.15)
ms:contentKeyID: 56558803
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Managing users and user account properties in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2015-03-09_

The following cmdlets manage Skype for Business Online user accounts.


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
<td><p><a href="get-csonlineuser.md">Get-CsOnlineUser</a></p></td>
<td><p>Returns information about users who have accounts homed with your Skype for Business Online tenant.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-csuseracp.md">Get-CsUserAcp</a><br />
<a href="remove-csuseracp.md">Remove-CsUserAcp</a><br />
<a href="set-csuseracp.md">Set-CsUserAcp</a></p></td>
<td><p>Enables you to assign, modify, or unassign an audio conferencing provider to individual users.</p>
<p>An audio conferencing provider is a third-party company that provides organizations with conferencing services, including high-end services such as live translation, transcription, and live per-conference operator assistance.</p>
<p>These cmdlets do not return information about the audio providers available to be assigned to those users. For that information, run this command instead:</p>
<pre><code>Get-CsAudioConferencingProvider</code></pre></td>
</tr>
</tbody>
</table>


<div class="alert">


> [!WARNING]
> The Set-CsUser cmdlet is also included in the set of cmdlets available to Skype for Business Online administrators. However, Set-CsUser cannot currently be used to manage Skype for Business Online, except for setting the AudioVideoDisabled parameter. If you attempt to run the cmdlet with any other parameter, it will fail along with an error message similar to this:<BR>Unable to set “SipAddress”. This parameter is restricted within Remote Tenant PowerShell.”



</div>

Audio conferencing providers can also be assigned to (or unassigned from) user accounts by using the Skype for Business Online admin center:

![Lync admin center dial-in conferencing properties](images/Dn362790.0c61f0c2-8aef-4020-a0a8-02580d43092a(OCS.15).png "Lync admin center dial-in conferencing properties")

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

