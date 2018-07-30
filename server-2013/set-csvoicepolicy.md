---
title: Set-CsVoicePolicy
TOCTitle: Set-CsVoicePolicy
ms:assetid: e6035b74-d760-4c48-aa0b-d09d129e0830
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg399021(v=OCS.15)
ms:contentKeyID: 48185671
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsVoicePolicy

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-25_

Modifies an existing voice policy. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsVoicePolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsVoicePolicy [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AllowCallForwarding <$true | $false>] [-AllowPSTNReRouting <$true | $false>] [-AllowSimulRing <$true | $false>] [-CallForwardingSimulRingUsageType <VoicePolicyUsage | InternalOnly | CustomUsage>] [-Confirm [<SwitchParameter>]] [-CustomCallForwardingSimulRingUsages <PSListModifier>] [-Description <String>] [-EnableBWPolicyOverride <$true | $false>] [-EnableCallPark <$true | $false>] [-EnableCallTransfer <$true | $false>] [-EnableDelegation <$true | $false>] [-EnableMaliciousCallTracing <$true | $false>] [-EnableTeamCall <$true | $false>] [-EnableVoicemailEscapeTimer <$true | $false>] [-Force <SwitchParameter>] [-Name <String>] [-PreventPSTNTollBypass <$true | $false>] [-PstnUsages <PSListModifier>] [-PSTNVoicemailEscapeTimer <Int64>] [-Tenant <Guid>] [-VoiceDeploymentMode <OnPrem | Online | OnlineBasic | OnPremOnlineHybrid>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example sets the AllowSimulRing property to False for the per-user policy UserVoicePolicy2, meaning any users assigned this policy are not enabled for simultaneous ring, a feature that determines whether a second phone (such as a mobile phone) can be set to ring every time the user’s office phone rings. This command also removes "Local" from the list of PSTN usages for this policy. (Note that the Identity parameter is not explicitly specified. The Identity parameter is a positional parameter, therefore if you put the identity value first in the list of parameters you don’t need to explicitly state that it’s the Identity.)

    Set-CsVoicePolicy UserVoicePolicy2 -AllowSimulRing $false -PstnUsages @{remove="Local"}

</div>

<div>

## EXAMPLE 2

This example modifies the voice policy for site Redmond so that all the PSTN usages defined for the organization are applied to this policy. The first line in this example calls the **Get-CsPstnUsage** cmdlet to retrieve the global set of PSTN usages for the organization and save that set in the variable $a. The second line calls the **Set-CsVoicePolicy** cmdlet to modify the voice policy for site Redmond. A value is passed to the PstnUsages parameter to replace the current list of usages for the policy with the list contained in the global set of PSTN usages. Note the syntax of the replace value: $a.Usage. This refers to the Usage property of the PSTN usage settings, which contains the list of PSTN usages.

    $a = Get-CsPstnUsage
    Set-CsVoicePolicy -Identity site:Redmond -PstnUsages @{replace=$a.Usage}

</div>

</div>

<div>

## Detailed Description

This cmdlet modifies an existing voice policy. Voice policies are used to manage such Enterprise Voice-related features as simultaneous ringing (the ability to have a second phone ring each time someone calls your office phone) and call forwarding. Use this cmdlet to change the settings that enable and disable many of these features.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsVoicePolicy** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsVoicePolicy"}

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
<td><p><em>AllowCallForwarding</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>If this parameter is set to True, users assigned to this policy can forward calls. If this parameter is set to False, calls cannot be forwarded.</p></td>
</tr>
<tr class="even">
<td><p><em>AllowPSTNReRouting</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>When this parameter is set to True, calls made to internal numbers homed on another pool will be routed through the public switched telephone network (PSTN) when the pool or WAN is unavailable.</p></td>
</tr>
<tr class="odd">
<td><p><em>AllowSimulRing</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>Simultaneous ring is a feature that allows multiple phones to ring when a single number is dialed. Setting this parameter to True enables simultaneous ring. If this parameter is set to False, simultaneous ring cannot be configured for any user assigned to this policy.</p></td>
</tr>
<tr class="even">
<td><p><em>CallForwardingSimulRingUsageType</em></p></td>
<td><p>Optional</p></td>
<td><p>CallForwardingSimulRingUsageType</p></td>
<td><p>Provides a way for administrators to manage call forwarding and simultaneous ringing. Allowed values are:</p>
<p>* VoicePolicyUsage – The default voice policy usage is used to manage call forwarding and simultaneous ringing on all calls. This is the default value.</p>
<p>* InternalOnly – Call forwarding and simultaneous ringing are limited to calls made from one Lync user to another.</p>
<p>* CustomUsage. A custom PSTN usage will be used to manage call forwarding and simultaneous ringing. This usage must be specified using the CustomCallForwardingSimulRingUsages parameter.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>CustomCallForwardingSimulRingUsages</em></p></td>
<td><p>Optional</p></td>
<td><p>PSListModifier</p></td>
<td><p>Custom PSTN usage used to manage call forwarding and simultaneous ringing. To add a custom usage to voice policy use syntax similar to this:</p>
<p>-CustomCallForwardingSimulRingUsages @{Add=&quot;RedmondPstnUsage&quot;}</p>
<p>To remove a custom usage, use this syntax:</p>
<p>-CustomCallForwardingSimulRingUsages @{Remove=&quot;RedmondPstnUsage&quot;}</p>
<p>Note that the usage must exist before it can be used with the CustomCallForwardingSimulRingUsages parameter.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>A description of the voice policy.</p>
<p>Maximum length: 1040 characters.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableBWPolicyOverride</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>Policies can be set to limit bandwidth and set various other properties relating to network configuration. Setting this parameter to True will allow override of these policies. In other words, if this parameter is set to True no bandwidth checks will be made, calls will go through regardless of the call admission control (CAC) settings.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableCallPark</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>The Call Park application allows a call to be held, or parked, at a certain number within a range of numbers for later retrieval. Setting this parameter to True enables this application for users assigned this policy. If this parameter is set to False, users assigned to this policy cannot park calls that have been dialed to their phone number.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableCallTransfer</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>Determines whether calls can be transferred to another number. If this parameter is set to True, calls can be transferred; if the parameter is set to False, calls cannot be transferred.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableDelegation</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>Call delegation allows a user to answer calls for another user or make calls on the other user’s behalf. For example, a manager can set up call delegation so that all incoming calls ring both his or her phone and the phone of an administrator. Setting this parameter to True allows users with this policy to set up call delegation. Setting this parameter to False disables call delegation.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableMaliciousCallTracing</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>Malicious call tracing is a standard that is in place to trace calls that a user designates as malicious. These calls can be traced even if caller ID is blocked. The trace is available only to the proper authorities and not to the user. Setting this property to True enables the ability to set a trace on malicious calls.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableTeamCall</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>Team Call allows a user to designate a group of other users whose phones will ring when that user’s number is called. This feature is useful in teams where, for example, anyone from a team can answer incoming calls from customers. Setting this parameter to True enables this feature.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableVoicemailEscapeTimer</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>When set to True, calls to an unanswered mobile device will be routed to the organization voicemail instead of the mobile device provider's voicemail. If a call is answered &quot;too soon&quot; (that is, before the value configured for the PSTNVoicemailEscapeTimer property has elapsed) it will be assumed that the mobile device is not available and the call will be routed to the organization voicemail.</p>
<p>The default value is False.</p></td>
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
<td><p>A unique identifier specifying the scope, and in some cases the name, of the policy.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>Optional</p></td>
<td><p>VoicePolicy</p></td>
<td><p>Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values. This object must be of type VoicePolicy and can be retrieved by calling the <strong>Get-CsVoicePolicy</strong> cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>A friendly name describing this policy.</p></td>
</tr>
<tr class="odd">
<td><p><em>PreventPSTNTollBypass</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>PSTN tolls are more commonly known as long-distance charges. Organizations can sometimes bypass these tolls by implementing a Voice over Internet Protocol (VoIP) solution that enables branch offices to connect via network calls. Setting this parameter to True will send calls through PSTN and incur charges rather than going through the network and bypassing the tolls.</p></td>
</tr>
<tr class="even">
<td><p><em>PstnUsages</em></p></td>
<td><p>Optional</p></td>
<td><p>PSListModifier</p></td>
<td><p>A list of PSTN usages available to this policy. The PSTN usage ties a voice policy to a phone route.</p>
<p>Any string value can be placed into this list, as long as the value exists in the current global list of PSTN usages. (Duplicate strings are not allowed; all string must be unique.) The list of PSTN usages can be retrieved by calling the <strong>Get-CsPstnUsage</strong> cmdlet.</p>
<p>Keep in mind that if you use this parameter to remove all PSTN usages from the policy, users granted this policy will not be able to make outbound PSTN calls.</p></td>
</tr>
<tr class="odd">
<td><p><em>PSTNVoicemailEscapeTimer</em></p></td>
<td><p>Optional</p></td>
<td><p>Int64</p></td>
<td><p>Amount of time (in milliseconds) used to determine whether or not a call has been answered &quot;too soon.&quot; If a response is received within this time interval Lync Server will assume that the mobile device is not available and automatically switch the call to the organization's voicemail. If no response is received before the time interval is reached then the call will be allowed to proceed.</p>
<p>The default value is 1500 milliseconds.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>Optional</p></td>
<td><p>Guid</p></td>
<td><p>Globally unique identifier (GUID) of the Lync Online tenant account whose voice policy is to be modified. For example:</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>You can return the tenant ID for each of your tenants by running this command:</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
</tr>
<tr class="odd">
<td><p><em>VoiceDeploymentMode</em></p></td>
<td><p>Optional</p></td>
<td><p>VoiceDeploymentMode</p></td>
<td><p>Allowed values are:</p>
<p>* OnPrem</p>
<p>* Online</p>
<p>* OnlineBasic</p>
<p>* OnPremOnlineHybrid</p>
<p>The default value is OnPrem.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoicePolicy object. Accepts pipelined input of voice policy objects.

</div>

<div>

## Return Types

This cmdlet does not return a value or object. Instead, it configures instances of the Microsoft.Rtc.Management.WritableConfig.Voice.VoicePolicy object.

</div>

<div>

## See Also


[New-CsVoicePolicy](new-csvoicepolicy.md)  
[Remove-CsVoicePolicy](remove-csvoicepolicy.md)  
[Get-CsVoicePolicy](get-csvoicepolicy.md)  
[Grant-CsVoicePolicy](grant-csvoicepolicy.md)  
[Test-CsVoicePolicy](test-csvoicepolicy.md)  
[Get-CsPstnUsage](get-cspstnusage.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

