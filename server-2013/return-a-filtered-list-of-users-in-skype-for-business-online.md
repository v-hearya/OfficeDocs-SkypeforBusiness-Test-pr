---
title: Return a filtered list of users in Skype for Business Online
TOCTitle: Return a filtered list of users
ms:assetid: f2c4d13b-8601-4192-8b94-e9a57969da11
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362858(v=OCS.15)
ms:contentKeyID: 56558872
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Return a filtered list of users in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-05_

By using the [Get-CsOnlineUser](get-csonlineuser.md) cmdlet and the LdapFilter or Filter parameters, you can easily return information about a targeted set of users. For example, this command returns all the users who work in the Finance department:

    Get-CsOnlineUser -LdapFilter "department=Finance"

<div>

## See Also


[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

