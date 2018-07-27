---
title: Get-CsPstnUsage
TOCTitle: Get-CsPstnUsage
ms:assetid: 9dc82b88-303b-4678-8298-0dbc769f6781
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412734(v=OCS.15)
ms:contentKeyID: 48184918
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsPstnUsage

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-07_

Returns information about public switched telephone network (PSTN) usage records used in your organization. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsPstnUsage [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsPstnUsage [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This command returns the list of global PSTN usages available within the organization.

    Get-CsPstnUsage

</div>

<div>

## EXAMPLE 2

The command in this example returns a list of all defined PSTN usages, with one usage listed on each line of output. Calling the **Get-CsPstnUsage** cmdlet by itself returns the Identity and the Usage list. If the Usage list contains more than three or four entries, the list will be abbreviated in the output, similar to this:

Usage : {Internal, Local, Long Distance, International...}

Use the command in this example to display only a list of usages. The output will be similar to this:

Internal

Local

Long Distance

International

Restricted

    (Get-CsPstnUsage).Usage

</div>

<div>

## EXAMPLE 3

This command returns all the PSTN usage names that have the string "tern" somewhere within the name. For example, this command will return "Internal" and "International" but not "Local" or "Long Distance".

The first part of this command is the **Get-CsPstnUsage** cmdlet within parentheses, which means the first thing that happens is for all the PSTN usages to be retrieved. The .Usage property returns only the usage information for the PSTN usages, not the Identity. This list of usages is then piped to the **ForEach-Object** cmdlet, which looks at the usage strings one at a time. The If statement compares the current usage string to the string "\*tern\*" (the \* are wildcards) and displays any occurrence that matches that pattern.

    (Get-CsPstnUsage).Usage | ForEach-Object {if ($_ -like "*tern*") {$_}}

</div>

</div>

<div>

## Detailed Description

PSTN usages are string values that are used for call authorization. A PSTN usage links a voice policy to a route. The **Get-CsPstnUsage** cmdlet retrieves the list of all PSTN usages available within an organization.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsPstnUsage** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsPstnUsage"}

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
<td><p><em>Filter</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>The Filter parameter allows you to retrieve only those PSTN usages with an Identity matching a particular wildcard string. However, the only Identity available to PSTN usages is Global, so this parameter is not useful for this cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>The level at which these settings are applied. The only identity that can be applied to PSTN usages is Global.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the PSTN usage information from the local data store rather than the main Central Management store.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None.

</div>

<div>

## Return Types

The **Get-CsPstnUsage** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.PSTNUsages object.

</div>

<div>

## See Also


[Set-CsPstnUsage](set-cspstnusage.md)  
[Get-CsVoicePolicy](get-csvoicepolicy.md)  
[Get-CsVoiceRoute](get-csvoiceroute.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

