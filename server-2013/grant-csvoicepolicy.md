---
title: Grant-CsVoicePolicy
TOCTitle: Grant-CsVoicePolicy
ms:assetid: c8aa8d0f-6fb4-43f7-82b0-38d4da2d5611
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398828(v=OCS.15)
ms:contentKeyID: 48185383
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Grant-CsVoicePolicy

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-06-04_

Assigns a voice policy to one or more users or groups. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Grant-CsVoicePolicy -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-PassThru <SwitchParameter>] [-PolicyName <String>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example assigns the voice policy with the Identity VoicePolicyRedmond to the user with the display name Ken Myer.

    Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName VoicePolicyRedmond

</div>

<div>

## EXAMPLE 2

This example assigns the voice policy with the Identity VoicePolicyRedmond to all users in the Finance OU: OU=Finance,OU=NorthAmerica,DC=litwareinc,DC=com. The first part of the command calls the **Get-CsUser** cmdlet to retrieve all users enabled for Lync Server or Office Communications Server from the specified OU. This collection of users is then piped to the **Grant-CsVoicePolicy** cmdlet, which assigns the policy VoicePolicyRedmond to each of these users.

    Get-CsUser -OU "ou=Finance,ou=North America,dc=litwareinc,dc=com" | Grant-CsVoicePolicy -PolicyName VoicePolicyRedmond

</div>

</div>

<div>

## Detailed Description

This cmdlet assigns an existing per-user voice policy to a user. Voice policies are used to manage such Enterprise Voice-related features as simultaneous ringing (the ability to have a second phone ring each time someone calls your office phone) and call forwarding. Use this cmdlet to assign the settings that enable and disable these features for a specific user.

You can check whether a user has been granted a per-user voice policy by calling a command in this format: Get-CsUser "\<user name\>" | Select-Object VoicePolicy. For example:

Get-CsUser "Ken Myer" | Select-Object VoicePolicy

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Grant-CsVoicePolicy** cmdlet locally: RTCUniversalUserAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Grant-CsVoicePolicy"}

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
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>The Identity (unique identifier) of the user to whom the policy is being assigned.</p>
<p>User identities can be specified by using one of four formats: 1) The user's SIP address; 2) the user principal name (UPN); 3) the user's domain name and logon name, in the form domain\logon (for example, litwareinc\kenmyer); and, 4) the user's Active Directory display name (for example, Ken Myer).</p>
<p>Note that you can use the asterisk (*) wildcard character when using the Display Name as the user Identity. For example, the Identity &quot;* Smith&quot; would return all the users with the last name Smith.</p>
<p>Full Data Type: Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>DomainController</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Allows you to specify a domain controller. If no domain controller is specified, the first available will be used.</p></td>
</tr>
<tr class="even">
<td><p><em>PassThru</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Returns the results of the command. By default, this cmdlet does not generate any output.</p></td>
</tr>
<tr class="odd">
<td><p><em>PolicyName</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>The name (Identity) of the voice policy to be assigned to the user. (Note that this includes only the name portion of the Identity. Per-user policy identities include a prefix of tag: that should not be included with the PolicyName.)</p></td>
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

String. Accepts a pipelined string value representing the Identity of a user account to which the voice policy is being granted.

</div>

<div>

## Return Types

When used with the PassThru parameter, returns an object of type Microsoft.Rtc.Management.ADConnect.Schema.OCSADUserOrAppContact.

</div>

<div>

## See Also


[New-CsVoicePolicy](new-csvoicepolicy.md)  
[Remove-CsVoicePolicy](remove-csvoicepolicy.md)  
[Set-CsVoicePolicy](set-csvoicepolicy.md)  
[Get-CsVoicePolicy](get-csvoicepolicy.md)  
[Test-CsVoicePolicy](test-csvoicepolicy.md)  
[Get-CsUser](get-csuser.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

