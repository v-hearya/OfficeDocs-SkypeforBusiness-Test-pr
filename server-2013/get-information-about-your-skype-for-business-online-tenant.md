---
title: Get information about your Skype for Business Online tenant
TOCTitle: Get information about your Skype for Business Online tenant
ms:assetid: 06467515-9114-45bb-8d09-26a915c3fc4d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362768(v=OCS.15)
ms:contentKeyID: 56558801
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get information about your Skype for Business Online tenant

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-05_

To return information about your Skype for Business Online tenant call the [Get-CsTenant](get-cstenant.md) cmdlet, without any additional parameters:

    Get-CsTenant

To return just the tenant name and ID (the value of the TenantID parameter is required when running cmdlets such as [Set-CsTenantPublicProvider](set-cstenantpublicprovider.md) and [Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md)), use this command:

    Get-CsTenant | Select-Object Name, TenantID

<div>

## See Also


[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

