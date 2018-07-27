---
title: The user does not have permission to manage this tenant in Skype for Business Online
TOCTitle: The user does not have permission to manage this tenant
ms:assetid: 714ccf81-9451-4585-b62d-979f2a606315
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362812(v=OCS.15)
ms:contentKeyID: 56558829
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# The user does not have permission to manage this tenant in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-05_

You cannot make a remote Windows PowerShell connection to Skype for Business Online unless you are a member of the Tenant Administrators group. If you are not, your connection attempt will fail, and you'll receive the following error message:

    New-PSSession : [admin.vdomain.com] Processing data from remote server admin.vdomain.com failed with the following error message: The user 'user@foo.com' does not have permission to manage this tenant. Permissions can be granted by assigning the user to the appropriate RBAC role. For more information, see the about_Remote_Troubleshooting Help topic.

If you think that you are, or are supposed to be, a member of the Tenant Administrators group, you'll need to contact Office 365 Support.

<div>

## See Also


[Diagnosing and resolving connection problems with Skype for Business Online](diagnosing-and-resolving-connection-problems-with-skype-for-business-online.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

