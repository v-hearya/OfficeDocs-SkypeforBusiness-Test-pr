---
title: Cmdlets in Skype for Business Online that use a user identity and the tag scope
TOCTitle: Cmdlets that use a user identity and the tag scope
ms:assetid: 344a21b0-5301-4e77-853a-970bb1c11e1d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362781(v=OCS.15)
ms:contentKeyID: 56558838
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Cmdlets in Skype for Business Online that use a user identity and the tag scope

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-05_

The **Grant-Cs** cmdlets (used for assigning policies to users) require two identifiers: a user identity (the Identity parameter) and the identity of a per-user policy (the PolicyName parameter). For example, to assign the voice policy, RedmondVoicePolicy, to the user Ken Myer, you use the following command:

    Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName "RedmondVoicePolicy"

There are two things to keep in mind when assigning policies to users. First, only per-user policies can be assigned. You cannot assign the global policy to a user. For example, this command will fail:

    Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName "global"

This command fails because there is no need to assign the global policy. If you want to manage a user by using the global policy, just be sure that you do not assign that user a per-user policy. If no per-user policy has been assigned to a user, the user will automatically be managed by using the global policy.

<div class="alert">


> [!NOTE]
> What if the user has previously been assigned a per-user policy, and you want to unassign that policy and have the user managed by the global policy instead? In that case, you’ll first use the following syntax, which unassigns a per-user policy by granting that user a null policy:<BR>Grant-CsVoicePolicy –Identity "Ken Myer" –PolicyName $Null



</div>

Second, keep in mind that per-user policies are created at the tag scope. However, you can omit the tag **prefix** when specifying a policy name. These two commands are identical:

    Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName "tag:RedmondVoicePolicy"
    Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName "RedmondVoicePolicy"

If you would like to return the identities for all your per-user policies (or, at least, all the per-user policies of specified type, such as voice policies), use a command similar to this:

    Get-CsVoicePolicy -Filter "tag:*"

The following cmdlets make use of both a user Identity and the tag scope:

  - [Grant-CsClientPolicy](grant-csclientpolicy.md)

  - [Grant-CsConferencingPolicy](grant-csconferencingpolicy.md)

  - [Grant-CsDialPlan](grant-csdialplan.md)

  - [Grant-CsExternalAccessPolicy](grant-csexternalaccesspolicy.md)

  - [Grant-CsHostedVoicemailPolicy](grant-cshostedvoicemailpolicy.md)

  - [Grant-CsVoicePolicy](grant-csvoicepolicy.md)

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

