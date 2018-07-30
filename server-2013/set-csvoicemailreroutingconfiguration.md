---
title: Set-CsVoicemailReroutingConfiguration
TOCTitle: Set-CsVoicemailReroutingConfiguration
ms:assetid: c16a0d47-318b-46e4-991c-e4842403dbe3
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412948(v=OCS.15)
ms:contentKeyID: 48185306
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsVoicemailReroutingConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-25_

Modifies settings that provide public switched telephone network (PSTN) phone numbers to access Exchange UM Subscriber Access and Auto Attendant features. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsVoicemailReroutingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsVoicemailReroutingConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AutoAttendantNumber <String>] [-Confirm [<SwitchParameter>]] [-Enabled <$true | $false>] [-Force <SwitchParameter>] [-SubscriberAccessNumber <String>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example enables the voice mail rerouting configuration settings for the site Redmond1.

    Set-CsVoicemailReroutingConfiguration -Identity site:Redmond1 -Enabled $True

</div>

<div>

## EXAMPLE 2

This example modifies the voice mail rerouting settings that apply to the site Redmond1, setting the phone number for Subscriber Access to +14255551213.

    Set-CsVoicemailReroutingConfiguration -Identity site:Redmond1 -SubscriberAccessNumber "+14255551213"

</div>

</div>

<div>

## Detailed Description

This cmdlet allows you to modify settings that determine where Auto Attendant and Subscriber Access calls are rerouted to when IP connectivity to an Exchange UM server is lost.

Auto Attendant and Subscriber Access are features of Exchange UM. The Auto Attendant feature provides voice recognition and touch-tone control (dual-tone multifrequency, or DTMF) for outside callers to navigate a company’s phone system to reach the desired department or employee or, in Message Taking Mode, to accept messages for users. (Voice rerouting for Message Taking Mode is recommended.) Subscriber Access allows internal users to access their Microsoft Outlook mailbox from a phone. The numbers provided by these settings allow callers to leave voice mail messages for Enterprise Voice users (the AutoAttendantNumber setting) and for those users to retrieve voice mail even if the IP connectivity from the Lync Server deployment at a remote site to Exchange UM in the data center is unavailable (the SubscriberAccessNumber setting).

Note that these settings are not available unless the Enabled property has been set to True.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsVoicemailReroutingConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the RBAC roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsVoicemailReroutingConfiguration"}

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
<td><p><em>AutoAttendantNumber</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>Phone number of the Auto Attendant to which the voice mail deposit attempts should be re-routed.</p>
<p>The number supplied to this parameter must be a LineUri of an existing contact object.</p>
<p>Value must be a number beginning with a digit 1 through 9, optionally preceded by a plus (+), followed by any number of digits.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Enabled</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>Indicates whether attempts to access voice mail should be re-routed through PSTN when IP connectivity is down.</p></td>
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
<td><p>The unique identifier of the configuration you want to modify. For this cmdlet the Identity will be either Global or Site:&lt;site name&gt;, where &lt;site name&gt; is the name of the site to which the settings are applied.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Optional</p></td>
<td><p>VoicemailReroutingConfiguration</p></td>
<td><p>Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.</p>
<p>This object must be of type Microsoft.Rtc.Management.WritableConfig.Settings.ExumRouting.VoicemailReroutingConfiguration (which can be retrieved by calling the <strong>Get-CsVoicemailReroutingConfiguration</strong> cmdlet).</p></td>
</tr>
<tr class="odd">
<td><p><em>SubscriberAccessNumber</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>Subscriber Access number to which the voice mail retrieval attempts should be re-routed.</p>
<p>The number supplied to this parameter must be a LineUri of an existing contact object.</p>
<p>Value must be a number beginning with a digit 1 through 9, optionally preceded by a plus (+), followed by any number of digits.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.ExumRouting.VoicemailReroutingConfiguration object. Accepts pipelined input of voice mail rerouting configuration objects.

</div>

<div>

## Return Types

This cmdlet does not return a value. It modifies an object of type Microsoft.Rtc.Management.WritableConfig.Settings.ExumRouting.VoicemailReroutingConfiguration.

</div>

<div>

## See Also


[New-CsVoicemailReroutingConfiguration](new-csvoicemailreroutingconfiguration.md)  
[Remove-CsVoicemailReroutingConfiguration](remove-csvoicemailreroutingconfiguration.md)  
[Get-CsVoicemailReroutingConfiguration](get-csvoicemailreroutingconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

