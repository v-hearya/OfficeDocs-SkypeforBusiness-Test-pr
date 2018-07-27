---
title: Enable/disable conference recording in Skype for Business Online
TOCTitle: Enable/disable conference recording
ms:assetid: f6c5afab-081c-495c-97f7-135dcc2f6085
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362857(v=OCS.15)
ms:contentKeyID: 56558869
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Enable/disable conference recording in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-05_

If you do not want users to have the ability to record online conferences, use the [Set-CsMeetingConfiguration](set-csmeetingconfiguration.md) cmdlet and set the value of the AllowConferenceRecording parameter to False ($False):

    Set-CsMeetingConfiguration -AllowConferenceRecording $False

To restore the ability to record online conferences, set the value of the AllowConferenceRecording parameter to True ($True):

    Set-CsMeetingConfiguration -AllowConferenceRecording $True

<div>

## See Also


[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

