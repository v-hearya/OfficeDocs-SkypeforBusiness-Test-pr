---
title: Remove an audio conferencing provider previously assigned to a user in Skype for Business Online
TOCTitle: Remove an audio conferencing provider previously assigned to a user
ms:assetid: 85d59e6c-d646-4908-9767-adb48763f6de
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362808(v=OCS.15)
ms:contentKeyID: 56558821
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove an audio conferencing provider previously assigned to a user in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-05_

To remove all the audio conferencing providers assigned to a user, run the [Remove-CsUserAcp](remove-csuseracp.md) cmdlet without any parameters (other than the Identity parameter, which indicates the user in question):

    Remove-CsUserAcp -Identity "Ken Myer"

If a user has been assigned multiple audio conferencing providers, you can remove a single provider by including the Name parameter, followed by the name of the provider to be removed:

    Remove-CsUserAcp -Identity "Ken Myer" -Name "Contoso ACP"

<div>

## See Also


[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

