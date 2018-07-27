---
title: 'Lync Server 2013: Static routing cmdlets'
TOCTitle: Static routing cmdlets
ms:assetid: 71d5e0cd-8412-4383-818a-95b851a4da4b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg416492(v=OCS.15)
ms:contentKeyID: 48184496
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Static routing cmdlets in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-06-20_

With static routes, administrators can predetermine the network routes taken by SIP messages. When a message is received by a server, the server checks the message address and then forwards the message to the next hop server preconfigured by an administrator. If configured correctly, static routes help ensure timely, and accurate, delivery of messages, and with minimal overheard placed on servers.

<div>

## Static Routing Cmdlets

Unless otherwise instructed by Microsoft support personnel, static routes configured for Microsoft Lync Server 2013 should be created using the [New-CsStaticRoute](new-csstaticroute.md) cmdlet. After a route has been created, you can then use the CsStaticRoutingConfiguration cmdlets to add that route to a static routing collection.

**Static Routing**

  - <span></span>  
    [Get-CsSipResponseCodeTranslationRule](get-cssipresponsecodetranslationrule.md)

  - <span></span>  
    [New-CsSipResponseCodeTranslationRule](new-cssipresponsecodetranslationrule.md)

  - <span></span>  
    [Remove-CsSipResponseCodeTranslationRule](remove-cssipresponsecodetranslationrule.md)

  - <span></span>  
    [Set-CsSipResponseCodeTranslationRule](set-cssipresponsecodetranslationrule.md)

<!-- end list -->

  - <span></span>  
    [New-CsStaticRoute](new-csstaticroute.md)

<!-- end list -->

  - <span></span>  
    [Get-CsStaticRoutingConfiguration](get-csstaticroutingconfiguration.md)

  - <span></span>  
    [New-CsStaticRoutingConfiguration](new-csstaticroutingconfiguration.md)

  - <span></span>  
    [Remove-CsStaticRoutingConfiguration](remove-csstaticroutingconfiguration.md)

  - <span></span>  
    [Set-CsStaticRoutingConfiguration](set-csstaticroutingconfiguration.md)

<!-- end list -->

  - <span></span>  
    [New-CsSipProxyCustom](new-cssipproxycustom.md)

<!-- end list -->

  - <span></span>  
    [New-CsSipProxyRealm](new-cssipproxyrealm.md)

<!-- end list -->

  - <span></span>  
    [New-CsSipProxyTCP](new-cssipproxytcp.md)

<!-- end list -->

  - <span></span>  
    [New-CsSipProxyTLS](new-cssipproxytls.md)

<!-- end list -->

  - <span></span>  
    [New-CsSipProxyTransport](new-cssipproxytransport.md)

<!-- end list -->

  - <span></span>  
    [New-CsSipProxyUseDefault](new-cssipproxyusedefault.md)

<!-- end list -->

  - <span></span>  
    [New-CsSipProxyUseDefaultCert](new-cssipproxyusedefaultcert.md)

<!-- end list -->

  - <span></span>  
    [New-CsIssuedCertId](new-csissuedcertid.md)

</div>

<div>

## See Also


[Lync Server PowerShell Blog](http://go.microsoft.com/fwlink/p/?linkid=203150)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

