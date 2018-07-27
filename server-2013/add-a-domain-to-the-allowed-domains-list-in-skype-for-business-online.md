---
title: Add a domain to the allowed domains list in Skype for Business Online
TOCTitle: Add a domain to the allowed domains list
ms:assetid: 7b7f76c8-3047-40be-a938-8ac2868a6bc8
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362818(v=OCS.15)
ms:contentKeyID: 56558813
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Add a domain to the allowed domains list in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-07-01_

Adding a first domain to the allowed domains list is a three-step process. First, use the [New-CsEdgeDomainPattern](new-csedgedomainpattern.md) cmdlet to create a domain object for the domain to be added:

    $x = New-CsEdgeDomainPattern -Domain "fabrikam.com"

Next, use the [New-CsEdgeAllowList](new-csedgeallowlist.md) cmdlet to create a new allowed list that includes the domain object:

    $newAllowList = New-CsEdgeAllowList -AllowedDomain $x

Finally, use the [Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md) cmdlet to write the new allowed list to Skype for Business Online:

    Set-CsTenantFederationConfiguration -AllowedDomains $newAllowList

<div>

## See Also


[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

