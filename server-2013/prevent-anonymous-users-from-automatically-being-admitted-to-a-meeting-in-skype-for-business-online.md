---
title: Prevent anonymous users from automatically being admitted to a meeting in Skype for Business Online
TOCTitle: Prevent anonymous users from automatically being admitted to a meeting
ms:assetid: 23f120d2-4c39-4509-aa1f-4d186a525075
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362775(v=OCS.15)
ms:contentKeyID: 56558830
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Prevent anonymous users from automatically being admitted to a meeting in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-05_

To prevent anonymous users from automatically being admitted to an online meeting, use the [Set-CsMeetingConfiguration](set-csmeetingconfiguration.md) cmdlet and set the AdmitAnonymousUsersByDefault property to False ($False):

    Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False

To enable automatic admittance, set the AdmitAnonymousUsersByDefault property back to True ($True):

    Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True

<div>

## See Also


[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

