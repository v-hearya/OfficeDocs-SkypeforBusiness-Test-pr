---
title: New-CsImFilterConfiguration
TOCTitle: New-CsImFilterConfiguration
ms:assetid: 1964cbf9-d7f1-4b4e-99d1-951ac42d82fe
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398244(v=OCS.15)
ms:contentKeyID: 48183535
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsImFilterConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-25_

Creates a new instant messaging (IM) filter configuration. IM filters are used to prevent users from sending instant messages that contain active hyperlinks. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    New-CsImFilterConfiguration -Identity <XdsIdentity> [-Action <Allow | Block | Warn>] [-AllowMessage <String>] [-BlockFileExtension <$true | $false>] [-Confirm [<SwitchParameter>]] [-Enabled <$true | $false>] [-Force <SwitchParameter>] [-IgnoreLocal <$true | $false>] [-InMemory <SwitchParameter>] [-Prefixes <PSListModifier>] [-WarnMessage <String>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

In Example 1, the **New-CsImFilterConfiguration** cmdlet is used to create a new IM filter configuration with the Identity site:Redmond. (Because no additional parameters were specified, these settings will be created using the default values.)

    New-CsImFilterConfiguration -Identity site:Redmond

</div>

<div>

## EXAMPLE 2

In this command, the **New-CsImFilterConfiguration** cmdlet is used to create a new IM filter configuration with the Identity site:Redmond. Because the Prefixes parameter has been specified, the new configuration will contain all the default values--including the default prefixes to filter--plus two additional URI prefixes: rtsp: and urn:. We add these prefixes by using the add list modifier to add these prefixes to the default list.

    New-CsImFilterConfiguration -Identity site:Redmond -Prefixes @{add="rtsp:","urn:"}

</div>

<div>

## EXAMPLE 3

In this command, the **New-CsFileTransferFilterConfiguration** cmdlet is used to create a new IM filter configuration with the Identity site:Redmond. This example is similar to Example 2 except that the replace list modifier has been used instead of the add list modifier. This means that all the default URI prefixes will be replaced by these two prefixes (rtsp: and urn:). Therefore, only URIs with prefixes of rtsp: or urn: will be filtered within instant messages for the site Redmond.

    New-CsImFilterConfiguration -Identity site:Redmond -Prefixes @{replace="rtsp:","urn:"}

</div>

</div>

<div>

## Detailed Description

When sending instant messages, users can embed a Uniform Resource Identifier (URI) within the text of that message to refer other participants in the conversation to a particular website or share. Lync Server can be configured so that hyperlinks with certain prefixes are blocked or are not active. (In other words, the participants can’t simply click the link and be taken to the site the URI refers to; they must copy and paste the link manually into a browser.)

The **New-CsImFilterConfiguration** cmdlet allows you to define a list of URI prefixes that will be filtered, in addition to enabling and disabling filtering altogether, within a specific site. Calling the **New-CsImFilterConfiguration** cmdlet with only an Identity specified will create a new configuration with that identity, populating the Prefixes list for that site with a set of default prefixes that will be filtered.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsImFilterConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsImFilterConfiguration"}

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
<td><p>XdsIdentity</p></td>
<td><p>A unique identifier specifying the scope of the IM filter configuration. Global settings exist by default and cannot be re-created with the <strong>New-CsImFilterConfiguration</strong> cmdlet, but you can create site-level settings by specifying an Identity of site:&lt;site name&gt;, where &lt;site name&gt; is the name of the site to which the settings will be applied (for example, site:Redmond).</p>
<p>Full Data Type: Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
</tr>
<tr class="even">
<td><p><em>Action</em></p></td>
<td><p>Optional</p></td>
<td><p>UrlFilterAction</p></td>
<td><p>The value of this parameter determines the action that will be taken when a hyperlink is included in an instant message:</p>
<p>Allow - Hyperlinks are prefixed with an underscore so that the links are no longer active. If a message is specified in the AllowMessage property, that message will be inserted at the beginning of each instant message containing hyperlinks.</p>
<p>Block - Delivery of messages containing active hyperlinks are blocked and Lync Server sends an error message to the sender.</p>
<p>Warn - Messages containing active hyperlinks are delivered to the receiving participants, along with a warning message that is inserted at the beginning of those messages. The warning message can be specified using the WarnMessage property. If Warn is specified and no WarnMessage is entered, IM filtering is disabled, although the settings for the BlockFileExtension property will still be honored.</p>
<p>Default: Allow, unless a message contains more than 1,000 URLs, in which case the default is Block.</p>
<p>Full Data Type: Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.UrlFilterAction</p></td>
</tr>
<tr class="odd">
<td><p><em>AllowMessage</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>If a value is specified for this parameter, that string is inserted at the beginning of each message containing hyperlinks when the value of the Action property is set to Allow. You can use this message to notify users of things such as the potential dangers of clicking unknown links, or your organization's relevant policies and requirements.</p></td>
</tr>
<tr class="even">
<td><p><em>BlockFileExtension</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>If this parameter is set to True, a hyperlink that contains a file path with an extension specified by the Extensions property defined in the applicable file transfer filter configuration (retrieved by calling the <strong>Get-CsFileTransferFilterConfiguration</strong> cmdlet) is blocked and an error message is returned to the sender. If this parameter is set to False, no special check is made for file extensions.</p>
<p>Default: True</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>Enabled</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>Enables or disables this feature. If this parameter is set to True, instant messages will be scanned for hyperlinks and the rules in this configuration will be applied. If this parameter is set to False, messages will not be checked for hyperlinks.</p>
<p>Default: True</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suppresses any confirmation prompts that would otherwise be displayed before making changes.</p></td>
</tr>
<tr class="even">
<td><p><em>IgnoreLocal</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>The value of this parameter controls whether filtering is performed on local Intranet URIs passed in instant messages.If this parameter is set to True, any URI that is defined in the Intranet zone of the local computer is ignored. (The local computer is the Front End Server running the IM Filter application.) If this parameter is set to False, the specified filtering is applied to all hyperlinks.</p>
<p>Default: True</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet’s matching Set- cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>Prefixes</em></p></td>
<td><p>Optional</p></td>
<td><p>PSListModifier</p></td>
<td><p>The list of URI prefixes that will be filtered. Any hyperlink included in an instant message with a prefix matching one of the prefixes in this list will be filtered according to the specified settings.</p>
<p>Default: callto:, file:, ftp., ftp:, gopher:, href, http:, https:, ldap:, mailto:, news:, nntp:, sip:, sips:, tel:, telnet:, www*.</p></td>
</tr>
<tr class="odd">
<td><p><em>WarnMessage</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>This parameter contains the warning message that is inserted at the beginning of each instant message that contains hyperlinks when the value of the Action property is set to Warn. Typically this message would be used for such things as stating the potential dangers of clicking unknown links, or referring to your organization's relevant policies and requirements.</p></td>
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

None.

</div>

<div>

## Return Types

Creates an object of type Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.ImFilterConfiguration.

</div>

<div>

## See Also


[Remove-CsImFilterConfiguration](remove-csimfilterconfiguration.md)  
[Set-CsImFilterConfiguration](set-csimfilterconfiguration.md)  
[Get-CsImFilterConfiguration](get-csimfilterconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

