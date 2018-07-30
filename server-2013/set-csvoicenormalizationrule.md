---
title: Set-CsVoiceNormalizationRule
TOCTitle: Set-CsVoiceNormalizationRule
ms:assetid: 68850abb-4ac7-4ae1-bb6e-d991385f92a4
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398491(v=OCS.15)
ms:contentKeyID: 48184370
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsVoiceNormalizationRule

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Modifies a voice normalization rule. Voice normalization rules are used to convert a telephone dialing requirement (for example, dialing 9 to access an outside line) to the E.164 phone number format used by Lync Server. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsVoiceNormalizationRule [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsVoiceNormalizationRule [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-IsInternalExtension <$true | $false>] [-Pattern <String>] [-Priority <Int32>] [-Translation <String>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example sets the description of the rule Prefix Redmond on site Redmond to "Add a prefix to all numbers on site Redmond".

    Set-CsVoiceNormalizationRule -Identity "site:Redmond/Prefix Redmond" -Description "Add a prefix to all numbers on site Redmond"

</div>

<div>

## EXAMPLE 2

This example modifies the voice normalization rule with the Identity global/SeattleFourDigit. A new Description has been specified to reflect the modifications to the rule. In addition, a Translation value has been specified that modifies the rule to translate any number matching the existing pattern of this rule to the same number but with the prefix +1206556. For example, if the existing pattern matched any four-digit number and the number 1234 were entered, this rule would translate that extension to the number +12065561234.

    Set-CsVoiceNormalizationRule -Identity global/SeattleFourDigit -Description "Translate an internal four-digit extension" -Translation '+1206556$1'

</div>

<div>

## EXAMPLE 3

Example 3 changes the name of the normalization rule. Keep in mind that changing the name also changes the name portion of the Identity. The **Set-CsVoiceNormalizationRule** cmdlet doesn’t have a Name parameter, so in order to change the name we first call the **Get-CsVoiceNormalizationRule** cmdlet to retrieve the rule with the Identity global/RedmondFourDigit and assign the returned object to the variable $a. We then assign the string RedmondRule to the Name property of the object. Next, we pass the variable to the Instance parameter of the **Set-CsVoiceNormalizationRule** cmdlet to make the change permanent.

    $a = Get-CsVoiceNormalizationRule -Identity global/RedmondFourDigit
    $a.name = "RedmondRule"
    Set-CsVoiceNormalizationRule -Instance $a

</div>

</div>

<div>

## Detailed Description

This cmdlet modifies a named voice normalization rule. These rules are a required part of phone authorization and call routing. They define the requirements for converting (or translating) numbers from an internal Lync Server format to a standard (E.164) format. An understanding of regular expressions is helpful in order to define number patterns that will be translated.

Rules that are modified by using this cmdlet are part of the dial plan and, in addition to being accessible through the **Get-CsVoiceNormalizationRule** cmdlet, can also be accessed through the NormalizationRules property returned by a call to the **Get-CsDialPlan** cmdlet.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsVoiceNormalizationRule** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsVoiceNormalizationRule"}

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
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>A friendly description of the normalization rule.</p>
<p>Maximum string length: 512 characters.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses any confirmation prompts that would otherwise be displayed before making changes.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>A unique identifier for the rule. The Identity specified must include the scope followed by a slash followed by the name; for example: site:Redmond/Rule1, where site:Redmond is the scope and Rule1 is the name.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>Optional</p></td>
<td><p>NormalizationRule</p></td>
<td><p>Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values. This object must be of type NormalizationRule and can be retrieved by calling the <strong>Get-CsVoiceNormalizationRule</strong> cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>IsInternalExtension</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>If True, the result of applying this rule will be a number internal to the enterprise. If False, applying the rule results in an external number. This value is ignored if the value of the OptimizeDeviceDialing property of the associated dial plan is set to False.</p></td>
</tr>
<tr class="odd">
<td><p><em>Pattern</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>A regular expression that the dialed number must match in order for this rule to be applied.</p></td>
</tr>
<tr class="even">
<td><p><em>Priority</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Int32</p></td>
<td><p>The order in which rules are applied. A number might match more than one rule. This parameter sets the order in which the rules are tested against the number.</p></td>
</tr>
<tr class="odd">
<td><p><em>Translation</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>The regular expression pattern that will be applied to the number to convert it to E.164 format.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.NormalizationRule object. The **Set-CsVoiceNormalizationRule** cmdlet accepts pipelined input of voice normalization rule objects.

</div>

<div>

## Return Types

The **Set-CsVoiceNormalizationRule** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.NormalizationRule object.

</div>

<div>

## See Also


[New-CsVoiceNormalizationRule](new-csvoicenormalizationrule.md)  
[Remove-CsVoiceNormalizationRule](remove-csvoicenormalizationrule.md)  
[Get-CsVoiceNormalizationRule](get-csvoicenormalizationrule.md)  
[Test-CsVoiceNormalizationRule](test-csvoicenormalizationrule.md)  
[Set-CsDialPlan](set-csdialplan.md)  
[Get-CsDialPlan](get-csdialplan.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

