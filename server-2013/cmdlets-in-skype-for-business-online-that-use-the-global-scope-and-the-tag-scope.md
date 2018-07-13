---
title: Cmdlets in Skype for Business Online that use the global scope and the tag scope
TOCTitle: Cmdlets that use the global scope and the tag scope
ms:assetid: 1e2bc055-8a72-425e-967b-e253add7018c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362774(v=OCS.15)
ms:contentKeyID: 56558824
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Cmdlets in Skype for Business Online that use the global scope and the tag scope

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-08-19_

In Skype for Business Online, policies can be configured at either the *global scope* or at the *tag scope* (or *per-user scope*). When using the **Get-Cs** cmdlets, you do not have to specify a scope or identity. If you call one of these cmdlets without any parameters, then all the relevant items will be returned. For example, this command returns information about all your external access policies:

    Get-CsExternalAccessPolicy

You need to include only the Identity parameter or the Filter parameter if you want to limit the returned data. For example, to return only the global policy, use this command:

    Get-CsExternalAccessPolicy -Identity "global"

To return a per-user policy that has the Identity “RedmondAccessPolicy”, use this command:

    Get-CsExternalAccessPolicy -Identity "RedmondAccessPolicy"

<div>


> [!NOTE]
> When referencing a per-user policy, the tag <STRONG>prefix</STRONG> is optional. This syntax, which includes the prefix, is also valid:<BR>Get-CsExternalAccessPolicy –Identity "tag:RedmondAccessPolicy"



</div>

To return all policies except the global policies (that is, all the per-user policies), use this command:

    Get-CsExternalAccessPolicy -Filter "tag:*"

The following cmdlets operate against both the global scope and the per-user (tag) scope:

  - [Get-CsClientPolicy](get-csclientpolicy.md)

  - [Get-CsConferencingPolicy](get-csconferencingpolicy.md)

  - [Get-CsDialPlan](get-csdialplan.md)

  - [Get-CsExternalAccessPolicy](get-csexternalaccesspolicy.md)

  - [Get-CsHostedVoicemailPolicy](get-cshostedvoicemailpolicy.md)

  - [Get-CsPresencePolicy](get-cspresencepolicy.md)

  - [Get-CsVoicePolicy](get-csvoicepolicy.md)

<div>


> [!NOTE]
> Despite the name, dial plans are, functionally speaking, policies. The term <EM>dial plan</EM> is used instead of, for example, dialing policy, in order to preserve the terminology used with previous versions of Lync Server.



</div>

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

