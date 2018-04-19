---
title: Ability to connect to tenant has been disabled in Skype for Business Online
TOCTitle: Ability to connect to tenant has been disabled
ms:assetid: 7365d31b-173e-4339-b0a3-98ab73a9558f
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362820(v=OCS.15)
ms:contentKeyID: 56558807
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Ability to connect to tenant has been disabled in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-05_

To use Windows PowerShell in order to manage Skype for Business Online, the EnableRemotePowerShellAccess property of your tenant Windows PowerShell policy must be set to True. If it is not, your connection will fail, and you'll receive the following error message:

    New-PSSession : [admin.vdomain.com] Processing data from remote server admin.vdomain.com failed with the following error message: The ability to connect to this tenant by using a remote PowerShell session has been disabled. Please contact Lync Help to check Tenant Powershell Policy of this tenant. For more information, see the about_Remote_Troubleshooting Help topic.

If you see this error message, you'll need to contact Office 365 Support and get remote Windows PowerShell access enabled.

<div>

## See Also


[Diagnosing and resolving connection problems with Skype for Business Online](diagnosing-and-resolving-connection-problems-with-skype-for-business-online.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

