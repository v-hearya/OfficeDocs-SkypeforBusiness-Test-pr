﻿---
title: New-CsSipDomain
TOCTitle: New-CsSipDomain
ms:assetid: 385f0f23-397b-4d8d-b9b7-ec942cda4a99
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425857(v=OCS.15)
ms:contentKeyID: 48183841
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsSipDomain

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Creates a new SIP domain for use in your organization. SIP domains are domains authorized to send and receive SIP traffic, and are used when assigning SIP addresses to users. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    New-CsSipDomain -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-IsDefault <$true | $false>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 creates a new SIP domain, one that has the Identity fabrikam.com.

    New-CsSipDomain -Identity fabrikam.com

</div>

<div>

## EXAMPLE 2

Example 2 creates a new SIP domain named fabrikam.com and makes this new domain the default SIP domain. By making fabrikam.com the default domain, this command also "demotes" the domain that previously served as the default SIP domain. That’s because you can have only one default SIP domain.

    New-CsSipDomain -Identity fabrikam.com -IsDefault $True

</div>

</div>

<div>

## Detailed Description

In order to configure SIP addresses for your users (and thus enable them to use SIP-related software such as Lync 2013), you need two pieces of information: a user ID (for example, Ken.Myer) and a SIP domain (for example, litwareinc.com). The SIP domain used to construct a SIP address must be a domain, located within your Active Directory forest, that is authorized to send and receive SIP traffic. For example, suppose you have domains named litwareinc.com, fabrikam.com, and contoso.com, but only litwareinc.com has been identified as being a SIP domain. In that case, you cannot use a SIP address like sip:Ken.Myer@fabrikam.com or sip:Ken.Myer@contoso.com, at least not until fabrikam.com and contoso.com have been configured as valid SIP domains. That is something you can do by running the **New-CsSipDomain** cmdlet.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsSipDomain** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsSipDomain"}

</div>

<div>

## Parameters


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Required</th>
<th>Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Fully qualified domain name (FQDN) for the new SIP domain. For example: -Identity fabrikam.com.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="even">
<td><p><em>IsDefault</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Indicates whether the domain is the default SIP domain, the domain used by Lync Server any time a domain name is not explicitly stated. If set to True, the new domain will also become the new default domain</p>
<p>The default value for IsDefault is False. If you do not want to make the new domain the default domain you can simply leave out the parameter.</p>
<p>If you change the default SIP domain you will need to restart the RTCCAA and RTCCAS services.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Describes what would happen if you executed the command without actually executing the command.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **New-CsSipDomain** cmdlet does not accept pipelined data.

</div>

<div>

## Return Types

The **New-CsSipDomain** cmdlet reates new instances of the Microsoft.Rtc.Management.Xds.SipDomain object.

</div>

<div>

## See Also


[Get-CsSipDomain](get-cssipdomain.md)  
[Remove-CsSipDomain](remove-cssipdomain.md)  
[Set-CsSipDomain](set-cssipdomain.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

