---
title: Unassign a per-user policy previously assigned to a user in Skype for Business Online
TOCTitle: Unassign a per-user policy previously assigned to a user
ms:assetid: bdba1d22-28e4-4203-a109-a3fb408783d3
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362840(v=OCS.15)
ms:contentKeyID: 56558857
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Unassign a per-user policy previously assigned to a user in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-05_

If you want to unassign a per-user policy that was previously assigned to a user, rerun the appropriate **Grant-Cs** cmdlet (for example, the [Grant-CsVoicePolicy](grant-csvoicepolicy.md) cmdlet to unassign a voice policy), and set the PolicyName parameter to a null value ($Null):

    Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName $Null

To unassign voice policies from all your users, use this command:

    Get-CsOnlineUser | Grant-CsVoicePolicy -PolicyName $Null

When a policy is unassigned from a user, that user will then be managed by the global policy.

<div>

## See Also


[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

