---
title: Get-CsArchivingConfiguration
TOCTitle: Get-CsArchivingConfiguration
ms:assetid: e4951b81-2738-4cc2-87be-f8ee79da6c09
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg399012(v=OCS.15)
ms:contentKeyID: 48185729
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsArchivingConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Returns information about how (or if) instant messaging (IM) sessions are archived in your organization. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsArchivingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsArchivingConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 returns a collection of all the archiving configuration settings in use in your organization.

    Get-CsArchivingConfiguration

</div>

<div>

## EXAMPLE 2

In Example 2, the Identity parameter is used to limit the returned collection of archiving configuration settings to those settings that have the Identity site:Redmond.

    Get-CsArchivingConfiguration -Identity site:Redmond

</div>

<div>

## EXAMPLE 3

In Example 3, the Filter parameter is used to limit the returned collection of archiving configuration settings to settings that have been configured at the site scope. The parameter value "site:\*" limits the returned items to those that have an Identity that starts with the string value "site:".

    Get-CsArchivingConfiguration -Filter site:*

</div>

<div>

## EXAMPLE 4

This example uses the **Get-CsArchivingConfiguration** cmdlet to return a collection of all the archiving configuration settings that have been enabled for use in your organization. To do that, the command first calls the **Get-CsArchivingConfiguration** cmdlet without any parameters in order to return a collection of all your archiving configuration settings. That collection is then piped to the **Where-Object** cmdlet, which applies a filter that limits the returned data to those collections where the EnableArchiving property is not equal to "None". If EnableArchiving is set to "None", archiving has been disabled. If this property is set to any other value (either "IMOnly" or "ImAndWebConf") that means that archiving has been enabled.

    Get-CsArchivingConfiguration | Where-Object {$_.EnableArchiving -ne "None"}

</div>

</div>

<div>

## Detailed Description

Many organizations find it useful to keep a transcript of all the IM sessions carried out by their users (or a selected subset of users). For other organizations, it’s mandatory to keep such transcripts. For example, many organizations in the financial world are required by law to keep copies of all their electronic communications.

Lync Server gives you flexibility when it comes to archiving IM and web conferencing sessions. If you have deployed Archiving Server, you can use the various **CsArchivingConfiguration** cmdlets to enable and disable instant message archiving and to manage your archiving database. You can also suspend IM should archiving fail; this helps to ensure that you keep a record of all your electronic communications.

In order to archive IM sessions, you must set up at least one Archiving Server. After the Archiving Server is set up, you must perform two additional steps. First, you need to enable archiving at the appropriate scope (for details, see the **Set-CsArchivingConfiguration** cmdlet help topic). This might be the global scope; however, you can also configure custom archiving settings for different sites.

Second, you must use archiving policies to indicate which users will have their IM sessions archived. What happens if you enable archiving but do not assign any users a policy that specifies that their IM sessions should be archived? Literally, nothing happens: IM sessions will not be archived unless a policy is in force that requires IM sessions to be archived.

With the **Get-CsArchivingConfiguration** cmdlet, you can determine how IM session archiving has been configured in your organization.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsArchivingConfiguration** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself) run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsArchivingConfiguration"}

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
<td><p>Enables you to use wildcard characters in order to return a collection (or collections) of archiving configuration settings. To return a collection of all the settings configured at the site scope, use this syntax: -Filter site:*. To return a collection of all the settings that have the string value &quot;Canada&quot; somewhere in their Identity (the only property you can filter on) use this syntax: -Filter &quot;*Canada*&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Indicates the unique identifier for the collection of archiving settings you want to return. To refer to the global settings use this syntax: -Identity global. To refer to a collection configured at the site scope, use syntax similar to this: -Identity site:Redmond. To return information about the settings assigned to an individual Registrar pool use syntax: like this:</p>
<p>-Identity &quot;service:Registrar:atl-cs-001.litwareinc.com&quot;</p>
<p>Pool-level settings are available only in Lync Server 2013.</p>
<p>Note that you cannot use wildcards when specifying an Identity. If you need to use wildcards, then include the Filter parameter instead.</p>
<p>If this parameter is not specified, then the <strong>Get-CsArchivingConfiguration</strong> cmdlet returns a collection of all the archiving configuration settings in use in the organization.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the archiving configuration data from the local replica of the Central Management store rather than from the Central Management store itself.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Get-CsArchivingConfiguration** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Get-CsArchivingConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Archiving.ArchivingSettings object.

</div>

<div>

## See Also


[New-CsArchivingConfiguration](new-csarchivingconfiguration.md)  
[Remove-CsArchivingConfiguration](remove-csarchivingconfiguration.md)  
[Set-CsArchivingConfiguration](set-csarchivingconfiguration.md)  
[Set-CsArchivingServer](set-csarchivingserver.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

