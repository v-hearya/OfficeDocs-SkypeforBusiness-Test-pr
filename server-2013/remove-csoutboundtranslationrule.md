---
title: Remove-CsOutboundTranslationRule
TOCTitle: Remove-CsOutboundTranslationRule
ms:assetid: 73e0bd0d-2458-464a-9e6e-1868143aadc8
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398556(v=OCS.15)
ms:contentKeyID: 48184513
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsOutboundTranslationRule

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Removes an existing outbound translation rule. An outbound translation rule converts phone numbers to the local dialing format for interaction with private branch exchange (PBX) systems. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsOutboundTranslationRule -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example removes an existing outbound translation rule for site Redmond named Prefix Redmond. Identities are unique, so this command will delete a single rule.

    Remove-CsOutboundTranslationRule -Identity "site:Redmond/Prefix Redmond"

</div>

<div>

## EXAMPLE 2

This example removes all site-level outbound translation rules. The first part of the command is a call to the **Get-CsOutboundTranslationRule** cmdlet with a Filter of site:\*, which will return a collection of all rules with Identity values beginning with site:. This collection is then piped to the **Remove-CsOutboundTranslationRule** cmdlet, which removes each rule in the collection.

    Get-CsOutboundTranslationRule -Filter site:* | Remove-CsOutboundTranslationRule

</div>

</div>

<div>

## Detailed Description

Call this cmdlet to remove an existing outbound translation rule. Lync Server normalizes phone numbers to E.164 format. However, many private branch exchange (PBX) systems aren’t able to work with this format. Outbound translations rules translate the number to the local dialing format prior to sending the number to the Mediation Server or gateway.

Each outbound translation rule is associated with a trunk configuration. That means that using this cmdlet to remove a rule will remove it from the trunk configuration at the corresponding scope.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsOutboundTranslationRule** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsOutboundTranslationRule"}

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
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>The unique identifier of the outbound translation rule you want to remove. The Identity consists of the scope followed by a unique name within each scope. For example, site:Redmond/OutboundRule1.</p></td>
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
<td><p>Suppresses any confirmation prompts that would otherwise be displayed before making changes.</p></td>
</tr>
<tr class="even">
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

Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TranslationRule object. Accepts pipelined input of outbound translation rule objects.

</div>

<div>

## Return Types

This cmdlet does not return a value. It removes an object of type Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TranslationRule.

</div>

<div>

## See Also


[New-CsOutboundTranslationRule](new-csoutboundtranslationrule.md)  
[Set-CsOutboundTranslationRule](set-csoutboundtranslationrule.md)  
[Get-CsOutboundTranslationRule](get-csoutboundtranslationrule.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

