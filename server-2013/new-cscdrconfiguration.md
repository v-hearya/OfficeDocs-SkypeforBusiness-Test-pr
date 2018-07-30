---
title: New-CsCdrConfiguration
TOCTitle: New-CsCdrConfiguration
ms:assetid: e5890ac3-7a6c-4609-a866-84c39b76d3a9
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg399018(v=OCS.15)
ms:contentKeyID: 48185659
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsCdrConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Creates a new set of call detail recording (CDR) settings. CDR enables you to track usage of such things as peer-to-peer instant messaging sessions, Voice over Internet Protocol (VoIP) phone calls, and conferencing calls. This usage data includes information about who called whom, when they called, and how long they talked. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    New-CsCdrConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-EnableCDR <$true | $false>] [-EnablePurging <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-KeepCallDetailForDays <UInt32>] [-KeepErrorReportForDays <UInt32>] [-PurgeHourOfDay <UInt32>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command in Example 1 uses the **New-CsCdrConfiguration** cmdlet to create a new set of CDR settings with the Identity site:Redmond. In addition to the Identity site:Redmond, the new settings also have the EnableCDR property set to False. Because site settings take precedence over global settings, this means that CDR will not be used in the Redmond site, regardless of whether or not CDR has been enabled at the global scope.

    New-CsCdrConfiguration -Identity site:Redmond -EnableCDR $False

</div>

<div>

## EXAMPLE 2

Example 2 uses the InMemory parameter to demonstrate how you can create a new collection of CDR configuration settings that initially exist only in memory. To do this, the example first uses the **New-CsCdrConfiguration** cmdlet and the InMemory parameter to create a virtual collection of settings with the Identity site:Redmond. This virtual collection is stored in the variable $x; if the collection was not stored in a variable it would be created and then immediately disappear.

After the virtual collection has been created, the command shown in line 2 sets the value of the EnableCDR property to False ($False). In line 3,the **Set-CsCdrConfiguration** cmdlet is then used to transform the virtual collection $x into an actual collection of CDR configuration settings that is applied to the Redmond site. If the **Set-CsCdrConfiguration** cmdlet was not called, the virtual collection would disappear as soon as the Windows PowerShell session was terminated or the variable $x was deleted.

    $x = New-CsCdrConfiguration -Identity site:Redmond -InMemory
    $x.EnableCDR = $False
    Set-CsCdrConfiguration -Instance $x

</div>

</div>

<div>

## Detailed Description

Call detail recording (CDR) provides a way for you to track usage of Lync Server capabilities such as Voice over IP (VoIP) phone calls; instant messaging (IM); file transfers; audio/video (A/V) conferencing; and application sharing sessions. CDR (which is available only if you have deployed the Monitoring service) keeps track of usage information: it logs information such as the parties involved in the call; the length of the call; and whether or not any files were transferred. (However, CDR not make a recording of the call itself.)

CDR also keeps track of call error information: detailed diagnostic data for both peer-to-peer sessions and for conferencing calls.

As an administrator, you can determine whether or not CDR is used in your organization; if the Monitoring Service has been deployed, you can easily enable or disable CDR. In addition, you can make this decision globally (in which case CDR will either be enabled or disabled throughout the organization) or on a site-by-site basis; for example, you could use CDR in the Redmond site but not use CDR in the Paris site.

The **New-CsCdrConfiguration** cmdlet enables you to create new CDR setting collections at the site scope. (New settings cannot be created at the global scope.) Note that a site can only host a single collection of CDR settings. That means that you cannot create a new collection for the Redmond site if the site already has a set of CDR configuration settings. If you try this, the command will fail.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsCdrConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsCdrConfiguration"}

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
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Represents the unique identifier to be assigned to the new collection of CDR configuration settings. Because you can only create new collections at the site scope, the Identity will always be the prefix &quot;site:&quot; followed by the site name; for example &quot;site:Redmond&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableCDR</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Indicates whether or not CDR is enabled. The default value is True.</p></td>
</tr>
<tr class="even">
<td><p><em>EnablePurging</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Indicates whether or not CDR records will periodically be deleted from the CDR database. If True (the default value), records will be deleted after the time period specified by the properties KeepCallDetailForDays (CDR records) and the KeepErrorReportForDays (CDR errors). If False, CDR records will be maintained indefinitely.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="even">
<td><p><em>InMemory</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet’s matching Set- cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><em>KeepCallDetailForDays</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt32</p></td>
<td><p>Indicates the number of days that CDR records will be kept in the CDR database; any records older than the specified number of days will automatically be deleted. (Note that purging will take place only if the EnablePurging property has been set to True.)</p>
<p>KeepCallDetailForDays can be set to any integer value between 1 and 2562 days (approximately 7 years). The default value is 60.</p></td>
</tr>
<tr class="even">
<td><p><em>KeepErrorReportForDays</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt32</p></td>
<td><p>Indicates the number of days that CDR error reports are kept; any reports older than the specified number of days will automatically be deleted. CDR error reports are diagnostic reports uploaded by client applications such as Lync 2013.</p>
<p>You can set this property to any integer value between 1 and 2562 days (approximately 7 years). The default value is 60.</p></td>
</tr>
<tr class="odd">
<td><p><em>PurgeHourOfDay</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt32</p></td>
<td><p>Indicates the local time of day when expired records are deleted from the CDR database. The time of day is specified using a 24-hour clock, with 0 representing midnight (12:00 A.M.) and 23 representing 11:00 P.M. Note that you can only specify the hour of the day; that means that you can schedule purging to take place at 4:00 A.M. but you cannot schedule it to take place at 4:30 A.M. or 4:15 A.M. The default value is 2 (2:00 A.M.). It is recommended that purging take place during non-working hours.</p>
<p>Database purging takes place only if the EnablePurging property is set to True.</p></td>
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

None. The **New-CsCdrConfiguration** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

Creates instances of the Microsoft.Rtc.Management.WritableConfig.Settings.CallDetailRecording.CdrSettings object.

</div>

<div>

## See Also


[Get-CsCdrConfiguration](get-cscdrconfiguration.md)  
[Remove-CsCdrConfiguration](remove-cscdrconfiguration.md)  
[Set-CsCdrConfiguration](set-cscdrconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

