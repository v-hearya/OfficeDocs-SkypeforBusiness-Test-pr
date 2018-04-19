---
title: Enable/disable a specified public IM provider in Skype for Business Online
TOCTitle: Enable/disable a specified public IM provider
ms:assetid: 9d3e2607-01c0-4ae9-accc-39f03ce253bb
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362825(v=OCS.15)
ms:contentKeyID: 56558840
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Enable/disable a specified public IM provider in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-08-13_

Skype for Business Online enables you to establish federation with users on one or more of the following public instant messaging (IM) providers:

  - Windows Live network of Internet services

  - Yahoo\!

  - AOL

To allow federation with one or more of these providers, use the [Set-CsTenantPublicProvider](set-cstenantpublicprovider.md) cmdlet and set the value of the Provider property to one or more of these values:

  - Windows Live

  - Yahoo

  - AOL

For example, this command establishes federation with Windows Live and AOL:

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "AOL","WindowsLive"

Note that any time you want to add or remove a provider, you must include all the relevant federated providers in the command. For example, you might want to add Yahoo\! and you run this command:

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "Yahoo"

This command will leave Yahoo\! as the only federated provider, because that is the provider called out in the command. To establish federation with all three public IM providers, you must include all three providers:

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "Yahoo", "AOL","WindowsLive"

Note that you must include the Tenant parameter when calling the Set-CsTenantPublicProvider cmdlet; if you do not, you will be prompted to enter the Tenant ID. You can return the Tenant ID of your Skype for Business Online tenant by using this command:

    Get-CsTenant | Select-Object TenantID

Or, use this command to store the Tenant ID in a variable:

    $tenantID = (Get-CsTenant | Select-Object TenantID)

You can then use that variable (in this example, $tenantID) when calling Set-CsTenantPublicProvider:

    Set-CsTenantPublicProvider -Tenant $tenantID -Provider "Yahoo", "AOL","WindowsLive"

<div>

## See Also


[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

