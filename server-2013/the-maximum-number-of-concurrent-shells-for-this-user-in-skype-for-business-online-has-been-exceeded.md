---
title: The maximum number of concurrent shells for this user in Skype for Business Online has been exceeded
TOCTitle: The maximum number of concurrent shells for this user has been exceeded
ms:assetid: b309efe8-a214-41ea-a345-93e6a36e0cb1
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362837(v=OCS.15)
ms:contentKeyID: 56558853
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# The maximum number of concurrent shells for this user in Skype for Business Online has been exceeded

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-05_

Each administrator is allowed a maximum of three simultaneous remote connections to Skype for Business Online. If you have three remote Windows PowerShell connections up and running, any attempt to make a fourth simultaneous connection will fail, with the following error message:

    New-PSSession : [admin.vdomain.com] Connecting to remote server admin.vdomain.com failed with the following error message : The WS-Management service cannot process the request. The maximum number of concurrent shells for this user has been exceeded. Close existing shells or raise the quota for this user. For more information, see the about_Remote_Troubleshooting Help topic.

The only way to resolve this issue is to close one or more of the previous connections. When you are finished with a Skype for Business Online session, we recommend that you use the **Remove-PSSession** cmdlet to terminate the session. This will help you to prevent this issue.

<div>

## See Also


[Diagnosing and resolving connection problems with Skype for Business Online](diagnosing-and-resolving-connection-problems-with-skype-for-business-online.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

