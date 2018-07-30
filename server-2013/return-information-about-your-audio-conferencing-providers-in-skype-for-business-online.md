---
title: Return information about your audio conferencing providers in Skype for Business Online
TOCTitle: Return information about your audio conferencing providers
ms:assetid: df9c8fc0-8bb6-4416-a5cc-aa9b1601a688
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362848(v=OCS.15)
ms:contentKeyID: 56558866
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Return information about your audio conferencing providers in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-05_

To return information about the audio conferencing providers that have been assigned to a user, use the [Get-CsUserAcp](get-csuseracp.md) cmdlet and the following syntax:

    Get-CsUserAcp -Identity "Ken Myer" | Select-Object -ExpandProperty AcpInfo

<div>

## See Also


[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

