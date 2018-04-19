---
title: Remove-CsImFilterConfiguration
TOCTitle: Remove-CsImFilterConfiguration
ms:assetid: 0c6f5f69-ae41-46d6-b817-fa1c6751c615
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398171(v=OCS.15)
ms:contentKeyID: 48183390
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsImFilterConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Removes the specified instant messaging (IM) filter configuration. (IM filter settings are used to prevent users from sending instant messages that contain hyperlinks.) This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsImFilterConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

In Example 1, the **Remove-CsImFilterConfiguration** cmdlet is used to remove the IM filter configuration with the Identity site:Redmond. When an IM filter configuration is removed from a site, that site will automatically begin using the global settings in its place.

    Remove-CsImFilterConfiguration -Identity site:Redmond

</div>

<div>

## EXAMPLE 2

In Example 2, all the IM filter configurations at the site scope are removed. To carry out this task, the command first uses the **Get-CsImFilterConfiguration** cmdlet and the Filter parameter to return all the configurations at the site scope; the wildcard string site:\* tells the **Get-CsImFilterConfiguration** cmdlet to return only those configurations that have an Identity that begins with the string value site:. The filtered collection of configurations is then piped to the **Remove-CsImFilterConfiguration** cmdlet, which deletes each configuration in the collection.

    Get-CsImFilterConfiguration -Filter site:* | Remove-CsImFilterConfiguration

</div>

</div>

<div>

## Detailed Description

When sending instant messages, users can embed a Uniform Resource Identifier (URI) within the text of that message to refer other participants in the conversation to a particular website or share. Lync Server can be configured so that hyperlinks with certain prefixes are blocked or are not active. (In other words, the participants can’t simply click the link and be taken to the site the URI refers to; they must copy and paste the link manually into a browser.)

The **Remove-CsImFilterConfiguration** cmdlet removes the IM filter configuration for a specified identity (such as a specific site). Running this cmdlet against the Global identity will simply reset the global configuration to the default settings.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsImFilterConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsImFilterConfiguration"}

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
<td><p>The unique identity of the configuration to be removed. This will be either Global or Site:&lt;site name&gt; (where &lt;site name&gt; represents the name of the site to which the settings apply).</p>
<p>Full Data Type: Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses any confirmation prompts that would otherwise be displayed before making changes.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.ImFilterConfiguration object. Accepts pipelined input of IM filter configuration objects.

</div>

<div>

## Return Types

Removes an object of type Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.ImFilterConfiguration.

</div>

<div>

## See Also


[New-CsImFilterConfiguration](new-csimfilterconfiguration.md)  
[Set-CsImFilterConfiguration](set-csimfilterconfiguration.md)  
[Get-CsImFilterConfiguration](get-csimfilterconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

