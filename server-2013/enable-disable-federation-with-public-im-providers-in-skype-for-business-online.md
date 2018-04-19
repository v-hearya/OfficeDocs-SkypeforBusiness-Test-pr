---
title: Enable/disable federation with public IM providers in Skype for Business Online
TOCTitle: Enable/disable federation with public IM providers
ms:assetid: 8609682c-97d3-48e6-a243-d84c1f9c8419
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362809(v=OCS.15)
ms:contentKeyID: 56558823
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Enable/disable federation with public IM providers in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-08-13_

To enable your users to communicate with users who have accounts on a public instant messaging (IM) provider, use the [Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md) cmdlet and set the AllowPublicUsers property to True ($True):

    Set-CsTenantFederationConfiguration -AllowPublicUsers $True

Note that you must then use the [Set-CsTenantPublicProvider](set-cstenantpublicprovider.md) cmdlet to specify the public IM providers that your users will be allowed to communicate with.

To disable federation with public providers, set the AllowPublicUsers property back to false ($False):

    Set-CsTenantFederationConfiguration -AllowPublicUsers $False

<div>

## See Also


[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

