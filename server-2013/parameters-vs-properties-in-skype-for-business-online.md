---
title: Parameters vs. properties in Skype for Business Online
TOCTitle: Parameters vs. properties
ms:assetid: 65348f95-f4d4-40cd-8869-f9d72643792d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362796(v=OCS.15)
ms:contentKeyID: 56558806
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Parameters vs. properties in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-05_

When reviewing the help topics for the Skype for Business Online cmdlets, you'll sometimes see the terms *parameter* and *property* used interchangeably. Don’t be confused by this terminology: although the two are technically different, in Skype for Business Online, the terms essentially refer to the same thing.

Technically speaking, parameters are used when you run a cmdlet. For example, in the following Windows PowerShell command, EnableMicrosoftPushNotificationService and EnableApplePushNotificationService are parameters of the [Set-CsPushNotificationConfiguration](set-cspushnotificationconfiguration.md) cmdlet:

    Set-CsPushNotificationConfiguration -EnableMicrosoftPushNotificationService -EnableApplePushNotificationService $True

A property is an attribute of a Skype for Business Online object (for example, a collection of push notification configuration settings). Let’s say that you run this command:

    Set-CsPushNotificationConfiguration

When you do this, you’ll get back a collection of properties and their associated values, which will include the following items:

    EnableMicrosoftPushNotificationService : True
    EnableApplePushNotificationService     : True

As you can see, properties and parameters share the same name: you use the EnableMicrosoftPushNotificationService parameter to configure the value of the EnableMicrosoftPushNotificationService property.

<div>

## See Also


[An introduction to Windows PowerShell and Skype for Business Online](an-introduction-to-windows-powershell-and-skype-for-business-online.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

