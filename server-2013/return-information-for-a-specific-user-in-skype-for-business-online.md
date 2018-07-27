---
title: Return information for a specific user in Skype for Business Online
TOCTitle: Return information for a specific user
ms:assetid: 6c8c2190-8e62-4f92-bbe9-4f692bd7ebf5
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362803(v=OCS.15)
ms:contentKeyID: 56558825
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Return information for a specific user in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-05_

There are multiple ways of referencing a specific user account when calling the [Get-CsOnlineUser](get-csonlineuser.md) cmdlet. You can use the user’s Active Directory Domain Services display name:

    Get-CsOnlineUser -Identity "Ken Myer"

You can use the user’s SIP address:

    Get-CsOnlineUser -Identity "sip:kenmyer@litwareinc.com"

You can use the user’s user principal name (UPN):

    Get-CsOnlineUser -Identity "kenmyer@litwareinc.com"

<div>

## See Also


[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

