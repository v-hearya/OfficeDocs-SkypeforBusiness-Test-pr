---
title: Allow federation in Skype for Business Online with all domains
TOCTitle: Allow federation with all domains
ms:assetid: d26f1057-a76c-447a-9efe-72efdce4c15e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362855(v=OCS.15)
ms:contentKeyID: 56558863
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Allow federation in Skype for Business Online with all domains

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-08-13_

If you want your users to be allowed to communicate with users from any domain, you must do two things. First, use the [New-CsEdgeAllowAllKnownDomains](new-csedgeallowallknowndomains.md) cmdlet to create an instance of the AllowAllKnownDomains object:

    $x = New-CsEdgeAllowAllKnownDomains

After that, call the [Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md) cmdlet, and set the value of the AllowedDomains property to the variable (in this example, $x) that contains the AllowAllKnownDomains object:

    Set-CsTenantFederationConfiguration -AllowedDomains $x

<div>

## See Also


[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

