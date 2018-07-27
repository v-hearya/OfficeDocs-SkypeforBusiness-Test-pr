---
title: The maximum number of concurrent shells for this tenant in Skype for Business Online has been exceeded
TOCTitle: The maximum number of concurrent shells for this tenant has been exceeded
ms:assetid: a4c91ffa-fdcc-414c-b941-a0d36c906825
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362832(v=OCS.15)
ms:contentKeyID: 56558845
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# The maximum number of concurrent shells for this tenant in Skype for Business Online has been exceeded

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-05_

Although each administrator is allowed to have as many as three simultaneous connections to a Skype for Business Online tenant, no single tenant is allowed to have more than nine simultaneous connections. For example, three administrators might each have three open sessions. If a fourth administrator tries to make a connection (resulting in a total of 10 simultaneous connections), this attempt will fail, with the following error message:

    New-PSSession : [admin.vdomain.com] Connecting to remote server admin.vdomain.com failed with the following error message : The WS-Management service cannot process the request. The maximum number of concurrent shells for this tenant has been exceeded. Close existing shells or raise the quota for this tenant. For more information, see the about_Remote_Troubleshooting Help topic.

The only way to resolve this issue is to close one or more of the previous connections. When you are finished with a Skype for Business Online session, we recommend that you use the **Remove-PSSession** cmdlet to terminate that session. This will help you to prevent this issue.

<div>

## See Also


[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

