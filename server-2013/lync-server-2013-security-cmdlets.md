---
title: 'Lync Server 2013: Security cmdlets'
TOCTitle: Security cmdlets
ms:assetid: 9a6c654d-287d-434e-8d93-409f0d623f5a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398799(v=OCS.15)
ms:contentKeyID: 48184968
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Security cmdlets in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-09_

The security cmdlets included in Microsoft Lync Server 2013 are primarily used to manage authentication, and user rights and permissions. A wide variety of cmdlets are available for managing authentication, including cmdlets for certificate and personal identification number (PIN) authentication. In addition, a number of cmdlets enable you to use the new role-based access control (RBAC) feature to delegate administrative control of Lync Server.

<div>

## Security Cmdlets

Many management tasks that apply to security settings can be performed from the Lync Server Control Panel. One major exception is the user permission cmdlets. However, all security management tasks can be performed using cmdlets from the Lync Server Management Shell or from within a script; using a script enables you to automate certain tasks. The following is a list of cmdlets that relate directly to managing security settings:

**[Certificate and authentication cmdlets in Lync Server 2013](lync-server-2013-certificate-and-authentication-cmdlets.md)**

  - <span></span>  
    [Get-CsCertificate](get-cscertificate.md)

  - <span></span>  
    [Import-CsCertificate](import-cscertificate.md)

  - <span></span>  
    [Remove-CsCertificate](remove-cscertificate.md)

  - <span></span>  
    [Request-CsCertificate](request-cscertificate.md)

  - <span></span>  
    [Set-CsCertificate](set-cscertificate.md)

<!-- end list -->

  - <span></span>  
    [Test-CsCertificateConfiguration](test-cscertificateconfiguration.md)

<!-- end list -->

  - <span></span>  
    [Get-CsClientCertificate](get-csclientcertificate.md)

  - <span></span>  
    [Revoke-CsClientCertificate](revoke-csclientcertificate.md)

<!-- end list -->

  - <span></span>  
    [Lock-CsClientPin](lock-csclientpin.md)

  - <span></span>  
    [Set-CsClientPin](set-csclientpin.md)

  - <span></span>  
    [Unlock-CsClientPin](unlock-csclientpin.md)

<!-- end list -->

  - <span></span>  
    [Get-CsClientPinInfo](get-csclientpininfo.md)

<!-- end list -->

  - <span></span>  
    [New-CsKerberosAccount](new-cskerberosaccount.md)

<!-- end list -->

  - <span></span>  
    [Get-CsKerberosAccountAssignment](get-cskerberosaccountassignment.md)

  - <span></span>  
    [New-CsKerberosAccountAssignment](new-cskerberosaccountassignment.md)

  - <span></span>  
    [Remove-CsKerberosAccountAssignment](remove-cskerberosaccountassignment.md)

  - <span></span>  
    [Set-CsKerberosAccountAssignment](set-cskerberosaccountassignment.md)

  - <span></span>  
    [Test-CsKerberosAccountAssignment](test-cskerberosaccountassignment.md)

<!-- end list -->

  - <span></span>  
    [Set-CsKerberosAccountPassword](set-cskerberosaccountpassword.md)

<!-- end list -->

  - <span></span>  
    [Get-CsPinPolicy](get-cspinpolicy.md)

  - <span></span>  
    [Grant-CsPinPolicy](grant-cspinpolicy.md)

  - <span></span>  
    [New-CsPinPolicy](new-cspinpolicy.md)

  - <span></span>  
    [Remove-CsPinPolicy](remove-cspinpolicy.md)

  - <span></span>  
    [Set-CsPinPolicy](set-cspinpolicy.md)

<!-- end list -->

  - <span></span>  
    [Get-CsProxyConfiguration](get-csproxyconfiguration.md)

  - <span></span>  
    [New-CsProxyConfiguration](new-csproxyconfiguration.md)

  - <span></span>  
    [Remove-CsProxyConfiguration](remove-csproxyconfiguration.md)

  - <span></span>  
    [Set-CsProxyConfiguration](set-csproxyconfiguration.md)

<!-- end list -->

  - <span></span>  
    [Get-CsSipDomain](get-cssipdomain.md)

  - <span></span>  
    [New-CsSipDomain](new-cssipdomain.md)

  - <span></span>  
    [Remove-CsSipDomain](remove-cssipdomain.md)

  - <span></span>  
    [Set-CsSipDomain](set-cssipdomain.md)

**[User rights and permissions cmdlets in Lync Server 2013](lync-server-2013-user-rights-and-permissions-cmdlets.md)**

  - <span></span>  
    [Get-CsAdminRole](get-csadminrole.md)

  - <span></span>  
    [New-CsAdminRole](new-csadminrole.md)

  - <span></span>  
    [Remove-CsAdminRole](remove-csadminrole.md)

  - <span></span>  
    [Set-CsAdminRole](set-csadminrole.md)

  - <span></span>  
    [Update-CsAdminRole](update-csadminrole.md)

<!-- end list -->

  - <span></span>  
    [Get-CsAdminRoleAssignment](get-csadminroleassignment.md)

<!-- end list -->

  - <span></span>  
    [Grant-CsOUPermission](grant-csoupermission.md)

  - <span></span>  
    [Revoke-CsOUPermission](revoke-csoupermission.md)

  - <span></span>  
    [Test-CsOUPermission](test-csoupermission.md)

<!-- end list -->

  - <span></span>  
    [Grant-CsSetupPermission](grant-cssetuppermission.md)

  - <span></span>  
    [Revoke-CsSetupPermission](revoke-cssetuppermission.md)

  - <span></span>  
    [Test-CsSetupPermission](test-cssetuppermission.md)

**[Interoperability cmdlets in Lync Server 2013](lync-server-2013-interoperability-cmdlets.md)**

  - [Get-CsOAuthConfiguration](get-csoauthconfiguration.md)

  - [Set-CsOAuthConfiguration](set-csoauthconfiguration.md)

<!-- end list -->

  - [Get-CsOAuthServer](get-csoauthserver.md)

  - [New-CsOAuthServer](new-csoauthserver.md)

  - [Remove-CsOAuthServer](remove-csoauthserver.md)

  - [Set-CsOAuthServer](set-csoauthserver.md)

<!-- end list -->

  - [Get-CsPartnerApplication](get-cspartnerapplication.md)

  - [New-CsPartnerApplication](new-cspartnerapplication.md)

  - [Remove-CsPartnerApplication](remove-cspartnerapplication.md)

  - [Set-CsPartnerApplication](set-cspartnerapplication.md)

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

