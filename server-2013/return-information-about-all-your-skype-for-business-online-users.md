---
title: Return information about all your Skype for Business Online users
TOCTitle: Return information about all your Skype for Business Online users
ms:assetid: 0b59fadf-67e6-48ea-86f1-2efef500ebdf
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362769(v=OCS.15)
ms:contentKeyID: 56558802
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Return information about all your Skype for Business Online users

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-05_

To return information about all your users who have been enabled for Skype for Business Online, call the [Get-CsOnlineUser](get-csonlineuser.md) cmdlet without any additional parameters:

    Get-CsOnlineUser

To return information for a single, randomly-selected user (for example, to use this account for test purposes), call the **Get-CsOnlineUser** cmdlet and set the ResultSize parameter to 1:

    Get-CsOnlineUser -ResultSize 1

That causes the **Get-CsOnlineUser** cmdlet to return information for just one user, regardless of how many users you have in your organization. To return information for five users, set the value of the ResultSize parameter to 5:

    Get-CsOnlineUser -ResultSize 5

<div>

## See Also


[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

