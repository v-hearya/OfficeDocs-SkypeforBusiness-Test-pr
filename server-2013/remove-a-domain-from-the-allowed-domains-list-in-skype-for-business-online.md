---
title: Remove a domain from the allowed domains list in Skype for Business Online
TOCTitle: Remove a domain from the allowed domains list
ms:assetid: 04948582-363b-49bd-8305-166c4c1d0dd9
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362766(v=OCS.15)
ms:contentKeyID: 56558798
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove a domain from the allowed domains list in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-08-13_

Removing a domain from the allowed domains list involves a series of steps. First, you must use a command similar to the following, in order to retrieve a collection of all the domains currently on the list:

    $x = (Get-CsTenantFederationConfiguration).AllowedDomains

Next, run this command to review those domains:

``` 
$x
```

Take note of the numeric position of the domain to be removed. If the domain is the first domain in the list, then it has an index value of 0. If the domain is the second domain in the list, it has an index value of 1, and so on.

After you know the index number, use a command like the following to remove the specified domain, making sure to use the correct index number. This command removes the first domain in the list (index number 0):

    $x.AllowedDomain.RemoveAt(0)

Finally, call the [Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md) cmdlet to write your changes to Skype for Business Online:

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

