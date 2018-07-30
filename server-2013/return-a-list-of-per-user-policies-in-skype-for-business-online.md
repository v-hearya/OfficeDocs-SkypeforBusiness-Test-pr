---
title: Return a list of per-user policies in Skype for Business Online
TOCTitle: Return a list of per-user policies
ms:assetid: e95a2755-3501-40cc-a704-5ecd01839d76
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362856(v=OCS.15)
ms:contentKeyID: 56558867
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Return a list of per-user policies in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-22_

To return a list of available per-user policies, first select the appropriate **Get-Cs** cmdlet (for example, the [Get-CsVoicePolicy](get-csvoicepolicy.md) cmdlet, if you want to return per-user voice policies). Then use the following syntax to return the Identity for each per-user policy:

    Get-CsVoicePolicy -Filter "tag:*" | Select-Object Identity

Note that, because of different licensing agreements and different country/region restrictions, it’s possible that certain conferencing policies, external access policies, or mobility policies cannot be assigned to a particular user. To verify the per-user policies that can actually be assigned to a given user (for example, kenmyer@litwareinc.com) use one of the following commands (and the ApplicableTo parameter), as appropriate:

    Get-CsConferencingPolicy -ApplicableTo "kenmyer@litwareinc.com"
    Get-CsExternalAccessPolicy -ApplicableTo "kenmyer@litwareinc.com"
    Get-CsMobilityPolicy -ApplicableTo "kenmyer@litwareinc.com"

The preceding syntax returns only those per-user policies that can actually be assigned to Ken Myer.

<div>

## See Also


[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

