---
title: Skype for Business Online failed to connect to Live ID Server
TOCTitle: Failed to connect to Live ID Server
ms:assetid: 701af721-dd6a-4f48-96f9-94e89c644201
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362811(v=OCS.15)
ms:contentKeyID: 56558828
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Skype for Business Online failed to connect to Live ID Server

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-05_

There are typically three reasons why your connection attempt might fail with the following error message:

    Get-CsWebTicket : Failed to connect live id servers. Make sure proxy is enabled or machine has network connection to live id servers.

Often this error means that the Microsoft Online Services Sign-in Assistant is not running. You can verify the status of this service by running the following command from the Windows PowerShell prompt:

    Get-Service "msoidsvc"

If the service is not running, start the service by using this command:

    Start-Service "msoidsvc"

If the service is running, you might be encountering problems with the network connection between your computer and the Microsoft Live ID Authentication Server. To check this, open Internet Explorer and navigate to <https://login.microsoftonline.com/.> Try logging on to Office 365 from there. If this fails, you are probably experiencing network connection issues.

Less commonly, it is possible that the Connection URI for Microsoft Live ID Authentication Server has been configured to the wrong value. If you've already determined that the Sign-In Assistant is running and that you are not experiencing network connectivity issues, this might be the issue. In this case, contact Office 365 Support.

<div>

## See Also


[Diagnosing and resolving connection problems with Skype for Business Online](diagnosing-and-resolving-connection-problems-with-skype-for-business-online.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

