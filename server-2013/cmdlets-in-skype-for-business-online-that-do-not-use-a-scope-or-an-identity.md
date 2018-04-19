---
title: Cmdlets in Skype for Business Online that do not use a scope or an identity
TOCTitle: Cmdlets that do not use a scope or an identity
ms:assetid: 9c50c732-3c64-4b6a-96fd-8f528eb739ce
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362824(v=OCS.15)
ms:contentKeyID: 56558839
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Cmdlets in Skype for Business Online that do not use a scope or an identity

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-05_

The cmdlets used when modifying the allowed lists and blocked lists (lists that determine which outside organizations your users are allowed to communicate with) do not use either a scope or an Identity. In fact, the **New-CsEdgeAllowAllKnownDomains** cmdlet does not have any parameters whatsoever. The cmdlets that do not use either a scope or an Identity are:

  - [New-CsEdgeAllowAllKnownDomains](new-csedgeallowallknowndomains.md)

  - [New-CsEdgeAllowList](new-csedgeallowlist.md)

  - [New-CsEdgeDomainPattern](new-csedgedomainpattern.md)

Note that, with both the **New-CsEdgeAllowList** cmdlet and the **New-CsEdgeDomainPattern** cmdlet, you must include the Domain parameter. For example:

    $x = New-CsEdgeDomainPattern -Domain "fabrikam.com"

<div>

## See Also


[Identities, scopes, and tenants in Skype for Business Online](identities-scopes-and-tenants-in-skype-for-business-online.md)  
[The Skype for Business Online cmdlets](the-skype-for-business-online-cmdlets.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

