---
title: Enable/disable push notification to iPhones and Windows Phones in Skype for Business Online
TOCTitle: Enable/disable push notification to iPhones and Windows Phones
ms:assetid: 64482dcb-6354-4fb5-a2e4-1564b3d0e047
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362792(v=OCS.15)
ms:contentKeyID: 56558808
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Enable/disable push notification to iPhones and Windows Phones in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-05_

To disable push notifications from being sent to either iPhones or Windows Phones, use the [Set-CsPushNotificationConfiguration](set-cspushnotificationconfiguration.md) cmdlet and set the values of the EnableApplePushNotificationService and the EnableMicrosoftPushNotificationService properties to False ($False):

    Set-CsPushNotificationConfiguration -EnableApplePushNotificationService $False -EnableMicrosoftPushNotificationService $False

Note that iPhones and Windows phones can be set independently. For example, this command disables push notifications on iPhones, but enables those notifications on Windows Phones:

    Set-CsPushNotificationConfiguration -EnableApplePushNotificationService $False -EnableMicrosoftPushNotificationService $True

<div>

## See Also


[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

