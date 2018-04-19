---
title: Get-CsCdrConfiguration
TOCTitle: Get-CsCdrConfiguration
ms:assetid: 4af8ffa2-63d3-4873-8dac-5afede090d4f
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398298(v=OCS.15)
ms:contentKeyID: 48184082
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsCdrConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Returns information about your call detail recording (CDR) settings. CDR enables you to track usage of such things as peer-to-peer instant messaging sessions, Voice over Internet Protocol (VoIP) phone calls, and conferencing calls. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsCdrConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsCdrConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example uses the **Get-CsCdrConfiguration** cmdlet to return a collection of all the CDR settings configured for use in your organization.

    Get-CsCdrConfiguration

</div>

<div>

## EXAMPLE 2

Example 2 uses the Identity parameter to return a single collection of CDR settings: the settings with the Identity site:Redmond.

    Get-CsCdrConfiguration -Identity site:Redmond

</div>

<div>

## EXAMPLE 3

In Example 3, the Filter parameter is employed to return all the CDR settings that have been configured at the site scope. The filter value "site:\*" returns all the CDR settings that have an Identity that begins with the string value "site:". By definition, those are settings that have been configured at the site scope.

    Get-CsCdrConfiguration -Filter site:*

</div>

<div>

## EXAMPLE 4

Example 4 returns a collection of all the CDR settings where the KeepCallDetailForDays property is fewer than 30 days. To do this, the command first uses the **Get-CsCdrConfiguration** cmdlet to return a collection of all the CDR settings configured in the organization. That collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the KeepCallDetailForDays value is less than 30 days.

    Get-CsCdrConfiguration | Where-Object {$_.KeepCallDetailForDays -lt 30}

</div>

</div>

<div>

## Detailed Description

Call detail recording (CDR) provides a way for you to track usage of Lync Server capabilities such as Voice over IP (VoIP) phone calls; instant messaging (IM); file transfers; audio/video (A/V) conferencing; and application sharing sessions. CDR (which is available only if you have deployed the Monitoring service) keeps usage information: it logs information such as the parties involved in the call; the length of the call; and whether or not any files were transferred. (However, CDR does not make a recording of the call itself.)

CDR also keeps track of call error information: detailed diagnostic data for both peer-to-peer sessions and for conferencing calls.

As an administrator, you can determine whether or not CDR is used in your organization. If the Monitoring service has been deployed, you can enable or disable CDR. In addition, you can make this decision globally (in which case CDR will either be enabled or disabled throughout the organization) or on a site-by-site basis; for example, you could use CDR in the Redmond site but not use CDR in the Paris site.

The **Get-CsCdrConfiguration** cmdlet provides a way for you return detailed information about how CDR is used in your organization.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsCdrConfiguration** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsCdrConfiguration"}

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
<td><p>Enables you to use wildcard characters in order to return a collection of CDR configuration settings. For example, to return a collection of all the settings configured at the site scope, use this syntax: -Filter site:*. To return a collection of all the settings that have the string value &quot;Western&quot; somewhere in their Identity, use this syntax: -Filter *Western*.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Indicates the unique identifier for the collection of CDR configuration settings you want to return. To refer to the global settings, use this syntax: -Identity global. To refer to a collection configured at the site scope, use syntax similar to this: -Identity site:Redmond. Note that you cannot use wildcards when specifying an Identity. If you need to use wildcards then use the Filter parameter instead.</p>
<p>If this parameter is not specified then the <strong>Get-CsCdrConfiguration</strong> cmdlet returns a collection of all the CDR configuration settings currently in use in the organization.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the CDR configuration data from the local replica of the Central Management store rather than from the Central Management store itself.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Get-CsCdrConfiguration** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Get-CsCdrConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.CallDetailRecording.CdrSettings object.

</div>

<div>

## See Also


[New-CsCdrConfiguration](new-cscdrconfiguration.md)  
[Remove-CsCdrConfiguration](remove-cscdrconfiguration.md)  
[Set-CsCdrConfiguration](set-cscdrconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

