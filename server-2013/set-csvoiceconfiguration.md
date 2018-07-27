---
title: Set-CsVoiceConfiguration
TOCTitle: Set-CsVoiceConfiguration
ms:assetid: dbab35ac-9a55-41d2-a726-9a26b2ff8e85
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398967(v=OCS.15)
ms:contentKeyID: 48185567
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsVoiceConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-25_

Modifies a list of voice test configurations. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsVoiceConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsVoiceConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-VoiceTestConfigurations <PSListModifier>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

It takes several steps to modify a test voice configuration within a voice configuration. In this example, we start by retrieving the voice configuration object by calling the **Get-CsVoiceConfiguration** cmdlet. We assign the object retrieved (there will be only one) to the variable $a.

In line 2 of this example we retrieve the contents of the VoiceTestConfigurations property, which is a collection of voice test configuration objects, from variable $a. We then pipe that collection to the **Where-Object** cmdlet, where we search the collection for the voice test configuration object with a Name equal to the string TestConfig2. We assign that object to the variable $b.

Next, we modify the TestConfig2 voice test configuration object by assigning new values to the properties DialedNumber and ExpectedTranslatedNumber. By updating that object we’ve updated the object in variable $a. However, that object is still only in memory. As a final step, we need to save those changes by passing $a to the Instance parameter of the **Set-CsVoiceConfiguration** cmdlet.

This is not the recommended way of modifying a voice configuration. To modify a voice configuration, simply change the individual voice test configurations with the **Set-CsVoiceTestConfiguration** cmdlet, as shown here:

Set-CsVoiceTestConfiguration -Identity TestConfig2 -DialedNumber 5551212 -ExpectedTranslatedNumber +5551212

That one line will accomplish the same task shown in Example 1.

    $a = Get-CsVoiceConfiguration
    $b = $a.VoiceTestConfigurations | Where-Object {$_.Name -eq "TestConfig2"}
    $b.DialedNumber = "5551212"
    $b.ExpectedTranslatedNumber = "+5551212"
    Set-CsVoiceConfiguration -Instance $a

</div>

</div>

<div>

## Detailed Description

Voice test configurations are used to test a phone number against a specific voice policy, route, and dial plan. This cmdlet can be used to modify voice test configurations from a list containing all the voice test configurations for a Lync Server deployment.

This cmdlet modifies an object of type VoiceConfiguration. This object is simply a container object for voice test configurations. Therefore, the use of this cmdlet is not recommended. To modify voice configurations, modify the individual voice test configurations by calling the **Set-CsVoiceTestConfiguration** cmdlet.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsVoiceConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsVoiceConfiguration"}

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
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suppresses any confirmation prompts that would otherwise be displayed before making changes.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>XdsIdentity</p></td>
<td><p>The scope of this object. The only value possible for this parameter is Global.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Optional</p></td>
<td><p>VoiceConfiguration</p></td>
<td><p>A reference to a voice configuration (Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceConfiguration) object. An object of this type can be retrieved by calling the <strong>Get-CsVoiceConfiguration</strong> cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><em>VoiceTestConfigurations</em></p></td>
<td><p>Optional</p></td>
<td><p>PSListModifier</p></td>
<td><p>A list of all voice test configurations (Microsoft.Rtc.Management.WritableConfig.Policy.Voice.TestConfiguration objects) defined for the Lync Server deployment.</p>
<p>You should modify individual voice test configuration objects by using the <strong>Set-CsVoiceTestConfiguration</strong> cmdlet. That is the recommended way of modifying configurations in this list.</p></td>
</tr>
<tr class="even">
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

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceConfiguration object. The **Set-CsVoiceConfiguration** cmdlet accepts pipelined input of a voice configuration object.

</div>

<div>

## Return Types

The **Set-CsVoiceConfiguration** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceConfiguration object.

</div>

<div>

## See Also


[Remove-CsVoiceConfiguration](remove-csvoiceconfiguration.md)  
[Get-CsVoiceConfiguration](get-csvoiceconfiguration.md)  
[New-CsVoiceTestConfiguration](new-csvoicetestconfiguration.md)  
[Set-CsVoiceTestConfiguration](set-csvoicetestconfiguration.md)  
[Get-CsVoiceTestConfiguration](get-csvoicetestconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

