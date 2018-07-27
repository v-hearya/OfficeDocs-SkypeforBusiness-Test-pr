---
title: Set-CsClientVersionConfiguration
TOCTitle: Set-CsClientVersionConfiguration
ms:assetid: 7cd2e86f-2d31-4db2-9d0f-f1418fd4aba2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398623(v=OCS.15)
ms:contentKeyID: 48184619
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsClientVersionConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-07_

Modifies the specified collection of client version configuration settings. Client version configuration settings determine whether or not Lync Server checks the version number of each client application that logs on to the system. If client version filtering is enabled, then the ability of that client application to access the system will be based on settings configured in the appropriate client version policy. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsClientVersionConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsClientVersionConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-DefaultAction <Allow | AllowWithUrl | Block | BlockWithUrl>] [-DefaultURL <String>] [-Enabled <$true | $false>] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

In Example 1, the **Set-CsClientVersionConfiguration** cmdlet is used to modify the settings collection with the Identity "site:Redmond". In this case, the Enabled parameter is set to False in order to disable the client version configuration settings.

    Set-CsClientVersionConfiguration -Identity site:Redmond -Enabled $False

</div>

<div>

## EXAMPLE 2

In Example 2, the DefaultUrl property is modified for all the client version configuration settings currently in use in the organization. To do this, the command first calls the **Get-CsClientVersionConfiguration** cmdlet without any additional parameters in order to return all of the client version configuration settings. That information is then piped to the **Set-CsClientVersionConfiguration** cmdlet, which sets the value of the DefaultUrl for each configuration collection to https://litwareinc.com/csclients.

    Get-CsClientVersionConfiguration | Set-CsClientVersionConfiguration -DefaultURL "https://litwareinc.com/csclients"

</div>

<div>

## EXAMPLE 3

In Example 3, modifications are made to all the client version configuration settings where the DefaultAction is currently set to Block. To carry out this task, the command first uses the **Get-CsClientVersionConfiguration** cmdlet to return all of the client version configuration settings currently in use. That information is then piped to the **Where-Object** cmdlet, which picks out only those items where the DefaultAction property is equal to "Block". In turn, that filtered collection is then piped to the **Set-CsClientVersionConfiguration** cmdlet, which does two things to each item in the collection: 1) sets the DefaultAction to BlockWithUrl; and, 2) sets the DefaultUrl to https://litwareinc.com/csclients.

    Get-CsClientVersionConfiguration | Where-Object {$_.DefaultAction -eq "Block"} | Set-CsClientVersionConfiguration -DefaultAction "BlockWithUrl" -DefaultURL "https://litwareinc.com/csclients"

</div>

</div>

<div>

## Detailed Description

Lync Server gives administrators considerable leeway when it comes to specifying the client software (and, equally important, the version number of that software) that users can use to log on to the system. For example, there is no technical reason that requires users to log on to Lync Server by using Lync; there are no technical limitations that would prevent users from logging on by using Microsoft Office Communicator 2007 R2.

On the other hand, there might be some non-technical reasons why you would prefer that your users do not log on by using Office Communicator 2007 R2. For example, Office Communicator 2007 R2 does not support all of the features and capabilities found in Lync; as a result, users who log on with Office Communicator 2007 R2 will have a different experience than users who log on by using Lync. This can create difficulties for your users; it can also create difficulties for help desk personnel, who must provide support for a number of different client applications.

If this could be a problem for your organization you can employ client version filtering in order to specify which client applications can be used to log on to Lync Server. When you install Lync Server, a global set of client version configuration settings is installed and enabled. These settings are used to determine whether or not client version filtering is enabled. In addition to the global settings, client version configuration settings can also be applied at the site scope; in those instances, the site settings will have precedence over the global settings.

The **Set-CsClientVersionConfiguration** cmdlet enables you to modify an existing collection of client version configuration settings.

Note that client version configuration is not a security feature. The technology relies on self-reporting from client applications, and does not attempt to verify that an application is really the application and the version number of that application that it claims to be.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsClientVersionConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsClientVersionConfiguration"}

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
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>DefaultAction</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.DefaultAction</p></td>
<td><p>Indicates the action to be taken if a user tries to log on from a client application with a version number that cannot be found in the appropriate client version policy. DefaultAction must be set to one of the following values:</p>
<p>Allow. The client application will be allowed to log on.</p>
<p>AllowWithUrl. The client application will be allowed to log on. In addition, a message box will be displayed to the user that includes the URL of a webpage where that user can download an approved client application. The URL for this webpage should be specified as the value for the DefaultUrl property.</p>
<p>Block. The client application will be prevented from logging on.</p>
<p>BlockWithUrl. The client application will be prevented from logging on. However, the &quot;Access denied&quot; message box displayed to the user will include the URL of a webpage where that user can download an approved client application. The URL for this webpage should be specified as the value for the DefaultUrl property.</p>
<p>This property is ignored if the Enabled property is set to False. When the Enabled property is set to False, then no client version filtering of any kind takes place.</p></td>
</tr>
<tr class="odd">
<td><p><em>DefaultURL</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Specifies the URL of the webpage where users can download an approved client application. If specified, and if the DefaultAction is set to BlockWithURL, this URL will appear in the &quot;Access denied&quot; message box displayed any time a user tries to log on from an unsupported client application.</p></td>
</tr>
<tr class="even">
<td><p><em>Enabled</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Indicates whether client version filtering is enabled or disabled. If the Enabled property is True, then the server will check the version number of each client application that attempts to log on; the server will then allow or deny access based on the appropriate client version policy. If the Enabled property is False, then any client application capable of logging on will be allowed to log on.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Represents the unique identifier of the client version configuration settings to be modified. To modify the global settings, use syntax like this: -Identity global. To modify settings assigned to the site scope, use syntax similar to this: &quot;site:Redmond&quot;.</p>
<p>If this parameter is not included, the <strong>Set-CsClientVersionConfiguration</strong> cmdlet will automatically configure the global settings.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>Optional</p></td>
<td><p>ClientVersionPolicy objects</p></td>
<td><p>Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionConfiguration object. The **Set-CsClientVersionConfiguration** cmdlet accepts pipelined instances of the client version configuration object.

</div>

<div>

## Return Types

The **Set-CsClientVersionConfiguration** cmdlet does not return a value or object. Instead, the cmdlet configures instances of the Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionConfiguration object.

</div>

<div>

## See Also


[Get-CsClientVersionConfiguration](get-csclientversionconfiguration.md)  
[New-CsClientVersionConfiguration](new-csclientversionconfiguration.md)  
[Remove-CsClientVersionConfiguration](remove-csclientversionconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

