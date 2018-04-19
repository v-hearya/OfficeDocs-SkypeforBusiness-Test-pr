---
title: Cmdlets in Skype for Business Online that use a conferencing provider identity
TOCTitle: Cmdlets that use a conferencing provider identity
ms:assetid: be5621b6-ec11-4b12-83ec-075af269ca6a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362841(v=OCS.15)
ms:contentKeyID: 56558858
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Cmdlets in Skype for Business Online that use a conferencing provider identity

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-05_

To return information about all of the audio conferencing providers that your organization has contracted with, you can simply call the [Get-CsAudioConferencingProvider](get-csaudioconferencingprovider.md) cmdlet without any parameters:

    Get-CsAudioConferencingProvider

If you want to limit the returned data to a single provider (in this example, the provider Contoso Audio Services), then use the Identity parameter:

    Get-CsAudioConferencingProvider -Identity "Contoso Audio Services"

There is only one Skype for Business Online cmdlet that accepts an audio conferencing provider ID:

  - [Get-CsAudioConferencingProvider](get-csaudioconferencingprovider.md)

<div>

## See Also


[Identities, scopes, and tenants in Skype for Business Online](identities-scopes-and-tenants-in-skype-for-business-online.md)  
[The Skype for Business Online cmdlets](the-skype-for-business-online-cmdlets.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

