---
title: Managing Skype for Business Online meetings and conferences
TOCTitle: Managing Skype for Business Online meetings and conferences
ms:assetid: a4d0c070-4df2-47df-a1e2-6ce62600a287
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362833(v=OCS.15)
ms:contentKeyID: 56558846
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Managing Skype for Business Online meetings and conferences

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2015-03-09_

The following cmdlets can be used to manage meeting and conferencing settings:


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
<td><p><a href="disable-csmeetingroom.md">Disable-CsMeetingRoom</a><br />
<a href="enable-csmeetingroom.md">Enable-CsMeetingRoom</a><br />
<a href="get-csmeetingroom.md">Get-CsMeetingRoom</a><br />
<a href="set-csmeetingroom.md">Set-CsMeetingRoom</a></p></td>
<td><p>Manages endpoint devices for meeting rooms.</p>
<p>In Skype for Business Online, meeting rooms are self-contained computer appliances that are installed in conference rooms and supply advanced meeting capabilities. To manage these new endpoint devices you must, among other things, create and enable an Exchange resource mailbox account for the device, and then enable that resource account for Skype for Business Online.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-csaudioconferencingprovider.md">Get-CsAudioConferencingProvider</a></p></td>
<td><p>Returns information about the audio conferencing providers that your organization is contracted with.</p>
<p>An audio conferencing provider is a third-party company that provides organizations with conferencing services, including high-end services such as live translation, transcription, and live per-conference operator assistance.</p></td>
</tr>
<tr class="odd">
<td><p><a href="get-csmeetingconfiguration.md">Get-CsMeetingConfiguration</a><br />
<a href="set-csmeetingconfiguration.md">Set-CsMeetingConfiguration</a></p></td>
<td><p>Controls the type of meetings that users can create and determines how meetings deal with anonymous users and dial-in conferencing users.</p>
<p>Meetings (also called conferences) are an integral part of Skype for Business Online. With these cmdlets, for example, you can configure meetings so that dial-in users are not automatically admitted the meeting, but are instead routed to the meeting lobby. These dial-in users remain on hold in the lobby until a presenter admits them to the meeting.</p></td>
</tr>
</tbody>
</table>


You can also manage a small subset of meeting configuration properties by using the Skype for Business Online admin center:

![Lync admin center general options properties](images/Dn362833.acf90793-7ee4-4faf-b791-f149dd5df2a5(OCS.15).png "Lync admin center general options properties")

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

