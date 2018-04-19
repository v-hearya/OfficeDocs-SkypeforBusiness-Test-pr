---
title: Assign a per-user policy to a user in Skype for Business Online
TOCTitle: Assign a per-user policy to a user
ms:assetid: 37e07da7-6391-4d6d-a428-c70272897039
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362779(v=OCS.15)
ms:contentKeyID: 56558849
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Assign a per-user policy to a user in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-22_

To assign a per-user policy to a user, you must first select the appropriate **Grant-Cs** cmdlet. (For example, the [Grant-CsVoicePolicy](grant-csvoicepolicy.md), if you want to assign a per-user voice policy.) Run the cmdlet, making sure to specify both the Identity of the user to be assigned the policy and the name of the policy being assigned:

    Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName "RedmondVoicePolicy"

If you want to assign the same policy to all your users, use this syntax:

    Get-CsOnlineUser | Grant-CsVoicePolicy -PolicyName "RedmondVoicePolicy"

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

