---
title: Set-CsCpsConfiguration
TOCTitle: Set-CsCpsConfiguration
ms:assetid: 9c2c0ad1-12f8-47b6-a7ec-60d91c9685bf
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412721(v=OCS.15)
ms:contentKeyID: 48184981
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsCpsConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-25_

Modifies an existing collection of Call Park service settings. Call parking is a service that allows a user to "park" an incoming phone call. Parking a call transfers it to a number in a specified range, or orbit, and then immediately places the call on hold. Anyone (not just the person who originally answered the call) can resume the conversation from any telephone simply by entering the correct number. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsCpsConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsCpsConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-CallPickupTimeoutThreshold <TimeSpan>] [-Confirm [<SwitchParameter>]] [-EnableMusicOnHold <$true | $false>] [-Force <SwitchParameter>] [-MaxCallPickupAttempts <Int32>] [-OnTimeoutURI <String>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 modifies the Call Park service configuration with the Identity site:Redmond1 by setting the maximum number of times a parked call will ring back to the answering phone to 2. This is done by including the MaxCallPickupAttempts parameter and setting the parameter value to 2.

    Set-CsCpsConfiguration -Identity site:Redmond1 -MaxCallPickupAttempts 2

</div>

<div>

## EXAMPLE 2

Example 2 is a variation of the command shown in Example 1; in this case, however, we set all (not just one) Call Park service configurations to have a MaxCallPickupAttempts property value of 2. To do this, the **Get-CsCpsConfiguration** cmdlet is used to retrieve a collection of all the Call Park service settings in use in the organization. This collection is then piped to the **Set-CsCpsConfiguration** cmdlet, which takes each individual item in the collection and sets the value of the MaxCallPickupAttempts property to 2.

    Get-CsCpsConfiguration | Set-CsCpsConfiguration -MaxCallPickupAttempts 2

</div>

<div>

## EXAMPLE 3

This example modifies the call park configuration for site Redmond1 by setting the amount of time that will elapse before a parked call will ring back (contained in the CallPickupTimeoutThreshold property) to 45 seconds.

    Set-CsCpsConfiguration -Identity site:Redmond1 -CallPickupTimeoutThreshold 00:00:45

</div>

</div>

<div>

## Detailed Description

This cmdlet is used to modify an existing Call Park service configuration. A Call Park service configuration specifies what happens to a call once it’s parked. For example, if a parked call isn’t answered after a period of time, it can be automatically forwarded to someone else, such as an administrator, or to a Response Group. Calls can be configured to ring after a certain period of time to ensure the call isn’t forgotten. In addition, Call Park service can be configured to play music on hold to the caller while the call is parked.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsCpsConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsCpsConfiguration"}

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
<td><p><em>CallPickupTimeoutThreshold</em></p></td>
<td><p>Optional</p></td>
<td><p>TimeSpan</p></td>
<td><p>The amount of time that will elapse after a call has been parked before it will ring back to the phone on which the call was answered.</p>
<p>This must be entered in the format hh:mm:ss (hh = hours, mm = minutes, ss = seconds)</p>
<p>Minimum Value: 10 seconds (00:00:10); Maximum Value: 10 minutes (00:10:00)</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableMusicOnHold</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>Determines whether music plays for the caller while a call is parked.</p>
<p>Lync Server ships with a default Music on Hold file. You can change this file (thereby changing the music the caller hears while parked) with the <strong>Set-CsCallParkServiceMusicOnHoldFile</strong> cmdlet.</p></td>
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
<td><p>A unique identifier of the configuration you want to modify. The Identity specifies the scope at which the configuration is applied, either Global or a specific site (in the format site:&lt;sitename&gt;, such as site:Redmond).</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Optional</p></td>
<td><p>CallParkServiceSettings</p></td>
<td><p>An object reference to a Call Park service configuration object, of type Microsoft.Rtc.Management.WritableConfig.Settings.CallParkServiceSettings.CallParkServiceSettings. This object can be retrieved by calling the <strong>Get-CsCpsConfiguration</strong> cmdlet. The object can then be changed and the changes saved by passing the object back to the <strong>Set-CsCpsConfiguration</strong> cmdlet in this parameter.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxCallPickupAttempts</em></p></td>
<td><p>Optional</p></td>
<td><p>Int32</p></td>
<td><p>The number of times a parked call will ring back to the answering phone before giving up and forwarding the call to the fallback Uniform Resource Identifier (URI). The fallback URI is set with the OnTimeoutURI parameter.</p>
<p>Minimum Value: 1; Maximum Value: 10</p></td>
</tr>
<tr class="even">
<td><p><em>OnTimeoutURI</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The SIP address of the user or Response Group to which unanswered parked calls will be routed. The parked call will be routed after the number of ringbacks defined with the MaxCallPickupAttempts parameter. If that parameter is set to Null, the OnTimeoutURI will be ignored and the parked call will be disconnected after unsuccessful ringback attempts.</p>
<p>Values must be SIP URIs, beginning with the string sip:. For example, sip:rgs1@litwareinc.com.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.CallParkServiceSettings.CallParkServiceSettings object. Accepts pipelined input of Call Park service configuration objects.

</div>

<div>

## Return Types

Modifies an object of type Microsoft.Rtc.Management.WritableConfig.Settings.CallParkServiceSettings.CallParkServiceSettings.

</div>

<div>

## See Also


[New-CsCpsConfiguration](new-cscpsconfiguration.md)  
[Remove-CsCpsConfiguration](remove-cscpsconfiguration.md)  
[Get-CsCpsConfiguration](get-cscpsconfiguration.md)  
[Set-CsCallParkServiceMusicOnHoldFile](set-cscallparkservicemusiconholdfile.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

