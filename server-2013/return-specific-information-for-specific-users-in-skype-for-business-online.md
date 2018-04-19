---
title: Return specific information for specific users in Skype for Business Online
TOCTitle: Return specific information for specific users
ms:assetid: bbee85bd-d8a7-4b28-90d7-45c43eee48f6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362838(v=OCS.15)
ms:contentKeyID: 56558861
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Return specific information for specific users in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-05_

By default, the [Get-CsOnlineUser](get-csonlineuser.md) cmdlet returns a huge amount of information for each Skype for Business Online user account. If you are interested in only a subset of that information, pipe the returned data to the **Select-Object** cmdlet. For example, this command returns all the data for the user Ken Myer, then uses the **Select-Object** cmdlet to limit the information displayed onscreen to Ken’s Active Directory Domain Services display name and dial plan:

    Get-CsOnlineUser -Identity "Ken Myer" | Select-Object DisplayName, DialPlan

The following command returns the display name and dial plan for all your users.

    Get-CsOnlineUser | Select-Object DisplayName, DialPlan

To find the properties of a Skype for Business Online user account, use this command:

    Get-CsOnlineUser | Get-Member

<div>

## See Also


[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

