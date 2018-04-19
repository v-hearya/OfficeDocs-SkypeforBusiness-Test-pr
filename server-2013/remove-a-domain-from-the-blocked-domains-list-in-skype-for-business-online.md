---
title: Remove a domain from the blocked domains list in Skype for Business Online
TOCTitle: Remove a domain from the blocked domains list
ms:assetid: a11ea475-bb8b-44be-a5a5-4abb2fed42b8
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362830(v=OCS.15)
ms:contentKeyID: 56558844
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove a domain from the blocked domains list in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-08-13_

Two steps are required to remove a domain from the blocked domains list. First, you must use the [New-CsEdgeDomainPattern](new-csedgedomainpattern.md) cmdlet to create a domain object for the domain to be removed:

    $x = New-CsEdgeDomainPattern "fabrikam.com"

After creating this object, use the following syntax to remove the domain (in this example, the domain stored in the variable $x) from the blocked domains list:

    Set-CsTenantFederationConfiguration -BlockedDomains @{Remove=$x}

To remove all the domains from the blocked domains list, set the value of the BlockedDomains property to null ($Null):

    Set-CsTenantFederationConfiguration -BlockedDomains $Null

<div>

## See Also


[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

