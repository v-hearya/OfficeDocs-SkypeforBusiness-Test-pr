---
title: Set-CsVoiceTestConfiguration
TOCTitle: Set-CsVoiceTestConfiguration
ms:assetid: 7b95fc95-ec0e-4bb3-aed1-e8b72e305999
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398614(v=OCS.15)
ms:contentKeyID: 48184590
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsVoiceTestConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-25_

Modifies a test scenario you can use to test phone numbers against specified routes and rules. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsVoiceTestConfiguration [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsVoiceTestConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-DialedNumber <String>] [-ExpectedRoute <String>] [-ExpectedTranslatedNumber <String>] [-ExpectedUsage <String>] [-Force <SwitchParameter>] [-TargetDialplan <String>] [-TargetVoicePolicy <String>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example sets the dialed number of the voice test configuration for TestConfig1 to 14255551212. This is the number that will be checked against the voice policy and route to ensure normalization occurs as expected, as well as to ensure the correct routes and dial plans are being applied.

    Set-CsVoiceTestConfiguration -Identity TestConfig1 -DialedNumber 14255551212

</div>

<div>

## EXAMPLE 2

This example modifies settings for the voice test configuration TestConfig1. The command sets the TargetDialplan to the dial plan for site:Redmond1. Because a change in dial plan could mean a change in normalization rules, the ExpectedTranslationNumber has also been changed to reflect what is expected from the normalization rules for that dial plan.

    Set-CsVoiceTestConfiguration -Identity TestConfig1 -TargetDialplan site:Redmond1 -ExpectedTranslatedNumber "+912065551212"

</div>

</div>

<div>

## Detailed Description

Before implementing voice routes and voice policies, it's a good idea to test them out on various phone numbers to ensure the results are what you're expecting. You can do this by modifying test scenarios with this cmdlet.

The **Set-CsVoiceTestConfiguration** cmdlet modifies the voice route, usage, dial plan, and voice policy against which to test a specified phone number. All of this information can be defined and retrieved using other cmdlets, as specified in the parameter descriptions for this topic.

The configurations modified with this cmdlet are tested using the **Test-CsVoiceTestConfiguration** cmdlet.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsVoiceTestConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsVoiceTestConfiguration"}

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
<td><p><em>DialedNumber</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The phone number you want to use to test the policies, usages, and so on.</p>
<p>Must be 512 characters or fewer.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExpectedRoute</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The name of the voice route expected to be used during the configuration test. If a different route is used, based on the target dial plan and voice policy, the test will fail. You can retrieve available voice routes by calling the <strong>Get-CsVoiceRoute</strong> cmdlet.</p>
<p>Must be 256 characters or fewer.</p></td>
</tr>
<tr class="even">
<td><p><em>ExpectedTranslatedNumber</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The phone number in the format you expect to see it in after translation. This is the value of the DialedNumber parameter after normalization. If you run the <strong>Test-CsVoiceTestConfiguration</strong> cmdlet and the DialedNumber does not result in the value in ExpectedTranslatedNumber, the test will report as Fail.</p>
<p>Must be 512 characters or fewer.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExpectedUsage</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The name of the PSTN usage expected to be used during the configuration test. If a different PSTN usage is used, based on the target dial plan and voice policy, the test will fail. You can retrieve available usages by calling the <strong>Get-CsPstnUsage</strong> cmdlet.</p>
<p>Must be 256 characters or fewer.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suppresses any confirmation prompts that would otherwise be displayed before making changes.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>XdsGlobalRelativeIdentity</p></td>
<td><p>A string uniquely identifying the test scenario you want to modify.</p>
<p>The value of this parameter does not include scope because this object can be created only at the global scope. Therefore only a name is required.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Optional</p></td>
<td><p>TestConfiguration</p></td>
<td><p>An object of type Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration that contains an existing voice test configuration with the changes you’d like to make to that configuration. An object of this type can be retrieved by calling the <strong>Get-CsVoiceTestConfiguraton</strong> cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><em>TargetDialplan</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The Identity of the dial plan to be used for this test. Dial plans can be retrieved by calling the <strong>Get-CsDialPlan</strong> cmdlet.</p>
<p>Must be 40 characters or fewer.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetVoicePolicy</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The Identity of the voice policy against which to run this test. Voice policies can be retrieved by calling the <strong>Get-CsVoicePolicy</strong> cmdlet.</p>
<p>Must be 40 characters or fewer.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration object. Accepts pipelined input of voice test configuration objects.

</div>

<div>

## Return Types

This cmdlet returns an object of type Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration.

</div>

<div>

## See Also


[New-CsVoiceTestConfiguration](new-csvoicetestconfiguration.md)  
[Remove-CsVoiceTestConfiguration](remove-csvoicetestconfiguration.md)  
[Get-CsVoiceTestConfiguration](get-csvoicetestconfiguration.md)  
[Test-CsVoiceTestConfiguration](test-csvoicetestconfiguration.md)  
[Get-CsVoiceRoute](get-csvoiceroute.md)  
[Get-CsPstnUsage](get-cspstnusage.md)  
[Get-CsDialPlan](get-csdialplan.md)  
[Get-CsVoicePolicy](get-csvoicepolicy.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

