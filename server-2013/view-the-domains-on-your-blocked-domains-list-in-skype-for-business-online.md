---
title: View the domains on your blocked domains list in Skype for Business Online
TOCTitle: View the domains on your blocked domains list
ms:assetid: 67c65dbf-1a68-4c77-aabd-bed5001b4267
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362797(v=OCS.15)
ms:contentKeyID: 56558810
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# View the domains on your blocked domains list in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-05_

To view all of the domains on your blocked domains list, call the [Get-CsTenantFederationConfiguration](get-cstenantfederationconfiguration.md) cmdlet, and then pipe the returned data to the **Select-Object** cmdlet:

    Get-CsTenantFederationConfiguration | Select-Object -ExpandProperty BlockedDomains

<div>

## See Also


[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

