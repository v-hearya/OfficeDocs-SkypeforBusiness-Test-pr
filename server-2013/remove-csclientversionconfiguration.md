---
title: Remove-CsClientVersionConfiguration
TOCTitle: Remove-CsClientVersionConfiguration
ms:assetid: 42065d1d-a0ef-4fa4-826b-d65b14b343c9
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425925(v=OCS.15)
ms:contentKeyID: 48183965
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsClientVersionConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Removes the specified collection of client version configuration settings. Client version configuration settings determine whether or not Lync Server checks the version number of each client application that logs on to the system. If client version filtering is enabled, then the ability of that client application to access the system will be based on settings configured in the appropriate client version policy. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsClientVersionConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 deletes the client version configuration settings that have the Identity "site:Redmond".

    Remove-CsClientVersionConfiguration -Identity site:Redmond

</div>

<div>

## EXAMPLE 2

In Example 2 all the client version configuration settings that have been applied at the site scope are deleted. To accomplish this task the command first calls the **Get-CsClientVersionConfiguration** cmdlet and the Filter parameter; the filter value "site:\*" ensures that only client version configuration settings that have an Identity beginning with the string value "site:" will be returned. This filtered collection is then piped to the **Remove-CsClientVersionConfiguration** cmdlet, which deletes each item in the collection.

    Get-CsClientVersionConfiguration -Filter site:* | Remove-CsClientVersionConfiguration

</div>

<div>

## EXAMPLE 3

In Example 3, all the client version configuration settings that are currently disabled are deleted. To do this, the command first uses the **Get-CsClientVersionConfiguration** cmdlet to return a collection of all the client version configuration settings currently in use in the organization. After this data is returned, the collection is piped to the **Where-Object** cmdlet, which picks out only those settings where the Enabled property is equal to False. From there, the filtered collection is piped to the **Remove-CsClientVersionConfiguration** cmdlet, which deletes each item in the collection.

    Get-CsClientVersionConfiguration | Where-Object {$_.Enabled -eq $False} | Remove-CsClientVersionConfiguration

</div>

</div>

<div>

## Detailed Description

Lync Server gives administrators considerable leeway when it comes to specifying the client software (and, equally important, the version number of that software) that users can use to log on to the system. For example, there is no technical reason that requires users to log on to Lync Server by using Lync; from a technical standpoint, there is nothing to prevent people from logging on by using Microsoft Office Communicator 2007 R2.

However, there might be some non-technical reasons why you would prefer that your users do not log on by using Office Communicator 2007 R2. For example, Office Communicator 2007 R2 does not support all of the features and capabilities found in Lync; as a result, users who log on with Office Communicator 2007 R2 will have a different experience than users who log on by using Lync. This can create difficulties for your users; it can also create difficulties for help desk personnel, who must provide support for a number of different client applications.

If this could be a problem for your organization you can employ client version filtering in order to specify which client applications can be used to log on to Lync Server. When you install Lync Server, a global set of client version configuration settings is installed and enabled. In addition to the global settings, client version configuration settings can also be applied at the site scope.

Any site settings you create can later be deleted by using the **Remove-CsClientVersionConfiguration** cmdlet. Note that you can also run the **Remove-CsClientVersionConfiguration** cmdlet against the global settings. In that case, the global settings will not be removed; instead, the global properties will be reset to their default values.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsClientVersionConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsClientVersionConfiguration"}

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
<td><p>Unique identifier for the collection of client version configuration settings to be removed. To remove the global collection, use the following syntax: -Identity global. (Keep in mind that the global settings will not actually be removed; instead, the global properties will all be reset to their default values.) To remove a site collection, use syntax similar to this: -Identity site:Redmond. Note that you cannot use wildcards when specifying the Identity.</p></td>
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
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionConfiguration object. The **Remove-CsClientVersionConfiguration** cmdlet accepts pipelined instances of the client version configuration object.

</div>

<div>

## Return Types

None. Instead, the cmdlet deletes instances of the Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionConfiguration object.

</div>

<div>

## See Also


[Get-CsClientVersionConfiguration](get-csclientversionconfiguration.md)  
[New-CsClientVersionConfiguration](new-csclientversionconfiguration.md)  
[Set-CsClientVersionConfiguration](set-csclientversionconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

