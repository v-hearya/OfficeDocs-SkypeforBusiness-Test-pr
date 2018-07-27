---
title: Assign an audio conferencing provider to a user in Skype for Business Online
TOCTitle: Assign an audio conferencing provider to a user
ms:assetid: 60db6896-9c5c-4d64-ab7e-10d91748587c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362791(v=OCS.15)
ms:contentKeyID: 56558804
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Assign an audio conferencing provider to a user in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-05_

The [Set-CsUserAcp](set-csuseracp.md) cmdlet provides a way for you to assign an audio conferencing provider to a user:

    Set-CsUserAcp -Identity "Ken Myer" -TollNumber "12065551219" -TollFreeNumbers "18005550712" -ParticipantPasscode "p@ssw0rd" -Domain "sip.contoso.com" -Name "Contoso ACP"

This assignment will be meaningless unless you have already contracted with the specified provider.

<div>

## See Also


[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

