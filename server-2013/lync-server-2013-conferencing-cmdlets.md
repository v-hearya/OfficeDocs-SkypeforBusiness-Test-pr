---
title: 'Lync Server 2013: Conferencing cmdlets'
TOCTitle: Conferencing cmdlets
ms:assetid: 7ff94637-6319-4c45-9230-be34e8d81ede
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398641(v=OCS.15)
ms:contentKeyID: 48184640
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Conferencing cmdlets in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-09_

Microsoft Lync Server 2013 enables users to join conferences in two different ways: by using a conferencing application such as Lync 2013, or by dialing in using a telephone. Dial-in users are not be able to do such things as view slides or exchange instant messages, but they are able to fully participate in the audio portion of a conference.

<div>

## Conferencing Cmdlets

The **CsDialInConferencing** cmdlets are used to configure dial-in conferencing properties, including everything from specifying the phone numbers users can call in order to join a conference to the keypad commands available to them after they join a conference (for example, pressing 6 to mute or unmute their phone). Most of the other features of a conference (for example, can users record the conference, can users share applications during the conference, and so on) are managed by using the **CsConferencingPolicy** cmdlets.

**[Dial-in conferencing cmdlets in Lync Server 2013](lync-server-2013-dial-in-conferencing-cmdlets.md)**

  - <span></span>  
    [Get-CsConferenceDirectory](get-csconferencedirectory.md)

  - <span></span>  
    [Move-CsConferenceDirectory](move-csconferencedirectory.md)

  - <span></span>  
    [New-CsConferenceDirectory](new-csconferencedirectory.md)

  - <span></span>  
    [Remove-CsConferenceDirectory](remove-csconferencedirectory.md)

<!-- end list -->

  - <span></span>  
    [Test-CsDialInConferencing](test-csdialinconferencing.md)

<!-- end list -->

  - <span></span>  
    [Get-CsDialInConferencingAccessNumber](get-csdialinconferencingaccessnumber.md)

  - <span></span>  
    [New-CsDialInConferencingAccessNumber](new-csdialinconferencingaccessnumber.md)

  - <span></span>  
    [Remove-CsDialInConferencingAccessNumber](remove-csdialinconferencingaccessnumber.md)

  - <span></span>  
    [Set-CsDialInConferencingAccessNumber](set-csdialinconferencingaccessnumber.md)

<!-- end list -->

  - <span></span>  
    [Get-CsDialInConferencingConfiguration](get-csdialinconferencingconfiguration.md)

  - <span></span>  
    [New-CsDialInConferencingConfiguration](new-csdialinconferencingconfiguration.md)

  - <span></span>  
    [Remove-CsDialInConferencingConfiguration](remove-csdialinconferencingconfiguration.md)

  - <span></span>  
    [Set-CsDialInConferencingConfiguration](set-csdialinconferencingconfiguration.md)

<!-- end list -->

  - <span></span>  
    [Get-CsDialInConferencingDtmfConfiguration](get-csdialinconferencingdtmfconfiguration.md)

  - <span></span>  
    [New-CsDialInConferencingDtmfConfiguration](new-csdialinconferencingdtmfconfiguration.md)

  - <span></span>  
    [Remove-CsDialInConferencingDtmfConfiguration](remove-csdialinconferencingdtmfconfiguration.md)

  - <span></span>  
    [Set-CsDialInConferencingDtmfConfiguration](set-csdialinconferencingdtmfconfiguration.md)

<!-- end list -->

  - <span></span>  
    [Get-CsDialInConferencingLanguageList](get-csdialinconferencinglanguagelist.md)

**[Web conferencing cmdlets in Lync Server 2013](lync-server-2013-web-conferencing-cmdlets.md)**

  - <span></span>  
    [Get-CsConferenceDisclaimer](get-csconferencedisclaimer.md)

  - <span></span>  
    [Remove-CsConferenceDisclaimer](remove-csconferencedisclaimer.md)

  - <span></span>  
    [Set-CsConferenceDisclaimer](set-csconferencedisclaimer.md)

<!-- end list -->

  - <span></span>  
    [Set-CsConferenceServer](set-csconferenceserver.md)

<!-- end list -->

  - <span></span>  
    [Get-CsConferencingConfiguration](get-csconferencingconfiguration.md)

  - <span></span>  
    [New-CsConferencingConfiguration](new-csconferencingconfiguration.md)

  - <span></span>  
    [Remove-CsConferencingConfiguration](remove-csconferencingconfiguration.md)

  - <span></span>  
    [Set-CsConferencingConfiguration](set-csconferencingconfiguration.md)

<!-- end list -->

  - <span></span>  
    [Get-CsConferencingPolicy](get-csconferencingpolicy.md)

  - <span></span>  
    [Grant-CsConferencingPolicy](grant-csconferencingpolicy.md)

  - <span></span>  
    [New-CsConferencingPolicy](new-csconferencingpolicy.md)

  - <span></span>  
    [Remove-CsConferencingPolicy](remove-csconferencingpolicy.md)

  - <span></span>  
    [Set-CsConferencingPolicy](set-csconferencingpolicy.md)

<!-- end list -->

  - <span></span>  
    [Get-CsMeetingConfiguration](get-csmeetingconfiguration.md)

  - <span></span>  
    [New-CsMeetingConfiguration](new-csmeetingconfiguration.md)

  - <span></span>  
    [Remove-CsMeetingConfiguration](remove-csmeetingconfiguration.md)

  - <span></span>  
    [Set-CsMeetingConfiguration](set-csmeetingconfiguration.md)

<!-- end list -->

  - [Disable-CsMeetingRoom](disable-csmeetingroom.md)

  - [Enable-CsMeetingRoom](enable-csmeetingroom.md)

  - [Get-CsMeetingRoom](get-csmeetingroom.md)

  - [Move-CsMeetingRoom](move-csmeetingroom.md)

  - [Set-CsMeetingRoom](set-csmeetingroom.md)

<!-- end list -->

  - <span></span>  
    [Test-CsASConference](test-csasconference.md)

  - <span></span>  
    [Test-CsAVConference](test-csavconference.md)

  - <span></span>  
    [Test-CsDataConference](test-csdataconference.md)

  - <span></span>  
    [Test-CsWebApp](test-cswebapp.md)

  - <span></span>  
    [Test-CsWebAppAnonymous](test-cswebappanonymous.md)

  - <span></span>  
    [Test-CsWebScheduler](test-cswebscheduler.md)

</div>

<div>

## See Also


[Lync Server PowerShell Blog](http://go.microsoft.com/fwlink/p/?linkid=203150)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

