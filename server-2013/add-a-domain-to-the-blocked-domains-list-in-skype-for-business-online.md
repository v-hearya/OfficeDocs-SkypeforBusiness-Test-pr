---
title: Add a domain to the blocked domains list in Skype for Business Online
TOCTitle: Add a domain to the blocked domains list
ms:assetid: ea6ebeea-3031-4c42-9a2c-88eaab790636
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362853(v=OCS.15)
ms:contentKeyID: 56558871
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Add a domain to the blocked domains list in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-07-01_

To add a domain to the blocked domains list, use syntax similar to this:

    $x = New-CsEdgeDomainPattern "fabrikam.com"
    Set-CsTenantFederationConfiguration -BlockedDomains @{Add=$x}

As you can see, this command requires two steps. First, you use the [New-CsEdgeDomainPattern](new-csedgedomainpattern.md) to create a domain object representing the domain to be added to the blocked list. After that, you use the [Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md) cmdlet and the Add method to add that domain (in this example, the domain stored in the variable $x) to the list.

<div>

## See Also


[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

