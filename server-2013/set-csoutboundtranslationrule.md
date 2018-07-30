---
title: Set-CsOutboundTranslationRule
TOCTitle: Set-CsOutboundTranslationRule
ms:assetid: fbf82146-7884-418c-8239-66c0ca0f2ba6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg413073(v=OCS.15)
ms:contentKeyID: 48185947
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsOutboundTranslationRule

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-25_

Modifies an existing outbound translation rule. An outbound translation rule converts phone numbers to the local dialing format for interaction with private branch exchange (PBX) systems. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsOutboundTranslationRule [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsOutboundTranslationRule [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-Pattern <String>] [-Priority <Int32>] [-Translation <String>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example modifies the global outbound translation rule with the Identity site:Redmond/Prefix Redmond. We’ve included a Description explaining that this rule is for translating numbers from E.164 format to a seven-digit phone number. In addition, Pattern and Translation values have been specified, which will modify the existing values for these properties. These values translate an E.164 number (in this case 12 digits beginning with +1425), specified by the regular expression in the Pattern, to a seven-digit number by removing the first five digits. For example, the number +14255551212 would be translated to the number 5551212.

    Set-CsOutboundTranslationRule -Identity "site:Redmond/Prefix Redmond" -Description "Convert to seven digits" -Pattern '^\+1425(\d{7})$' -Translation '$1'

</div>

<div>

## EXAMPLE 2

This example modifies the Name property of an outbound translation rule. Note that this results in changing the Identity of this rule. The first command in this example is a call to the **Get-CsOutboundTranslationRule** cmdlet. We specify an Identity of site:Redmond\\OBR1, which will return one translation rule, the rule with the Identity given. Rather than display this rule, we assign it to the variable $a. Line 2 of this example assigns the string "Outbound Rule 1" to the Name property of variable $a, the variable containing a reference to rule site:Redmond/OBR1. In the last line of this example we call the **Set-CsOutboundTranslationRule** cmdlet, specifying the Instance parameter and passing it the variable $a. If we now call the **Get-CsOutboundTranslationRule** cmdlet with an Identity value of site:Redmond/OBR1, nothing will be returned. That’s because the rule with that Identity no longer exists, it’s been replaced by the same rule but with the Identity site:Redmond/Outbound Rule 1.

    $a = Get-CsOutboundTranslationRule -Identity "site:Redmond/OBR1"
    $a.Name = "Outbound Rule 1"
    Set-CsOutboundTranslationRule -Instance $a

</div>

</div>

<div>

## Detailed Description

Lync Server normalizes phone numbers to E.164 format. However, many private branch exchange (PBX) systems aren’t able to work with this format. Outbound translations rules translate the number to the local dialing format prior to sending the number to the Mediation Server or gateway. Call this cmdlet to modify an existing outbound translation rule.

Each outbound translation rule is associated with a trunk configuration. That means that using this cmdlet to modify a rule will impact the corresponding trunk configuration. More than one outbound translation rule can be associated with each configuration. Therefore, the Identity for each rule consists of a scope along with a name that is unique within the scope (in the format scope/name, for example site:Redmond/OBR1). The rule is automatically associated with the trunk configuration with the same scope. Calling the **Set-CsOutboundTranslationRule** cmdlet is the recommended way of changing outbound translation rules in a trunk configuration.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsOutboundTranslationRule** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsOutboundTranslationRule"}

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
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>A friendly description of the outbound translation rule. This description can be used to help administrators clearly identify the purpose of the rule.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suppresses any confirmation prompts that would otherwise be displayed before making changes.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>XdsIdentity</p></td>
<td><p>The unique identifier of the outbound translation rule you want to modify. The Identity consists of the scope followed by a unique name within each scope. For example, site:Redmond/OutboundRule1.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>Optional</p></td>
<td><p>TranslationRule</p></td>
<td><p>An object reference to an outbound translation rule. This object must be of type Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TranslationRule, which can be retrieved by calling the <strong>Get-CsOutboundTranslationRule</strong> cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>Pattern</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>A regular expression representing the number pattern to which the Translation will be applied.</p></td>
</tr>
<tr class="odd">
<td><p><em>Priority</em></p></td>
<td><p>Optional</p></td>
<td><p>Int32</p></td>
<td><p>If a number matches the Pattern of more than one outbound translation rule, rules are applied in priority order. Use this parameter to assign a priority to the rule.</p></td>
</tr>
<tr class="even">
<td><p><em>Translation</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>A regular expression that will be applied to the number matching the Pattern to prepare that number for outbound routing.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
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

This cmdlet does not return a value. It modifies an object of type Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TranslationRule.

</div>

<div>

## See Also


[New-CsOutboundTranslationRule](new-csoutboundtranslationrule.md)  
[Remove-CsOutboundTranslationRule](remove-csoutboundtranslationrule.md)  
[Get-CsOutboundTranslationRule](get-csoutboundtranslationrule.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

