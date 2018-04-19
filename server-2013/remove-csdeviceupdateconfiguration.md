---
title: Remove-CsDeviceUpdateConfiguration
TOCTitle: Remove-CsDeviceUpdateConfiguration
ms:assetid: 4335eb24-61a6-4e76-8242-edfd861d7d0b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425933(v=OCS.15)
ms:contentKeyID: 48183977
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsDeviceUpdateConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Removes the specified device update configuration settings. These settings help manage the Device Update Web service, a Lync Server component that enables administrators to distribute firmware updates to telephones and other devices running Lync Phone Edition. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsDeviceUpdateConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

In Example 1, the **Remove-CsDeviceUpdateConfiguration** cmdlet is used to "remove" the global device update configuration settings. Because the global settings cannot actually be removed, the command will not delete anything; however, all the properties in the global device update configuration settings will be reset to their default values.

    Remove-CsDeviceUpdateConfiguration -Identity global

</div>

<div>

## EXAMPLE 2

The command shown in Example 2 removes the device update configuration settings with the Identity site:Redmond. Because these settings were configured at the site scope, they will be deleted, and the Redmond site will no longer have its own set of device update configuration settings.

    Remove-CsDeviceUpdateConfiguration -Identity site:Redmond

</div>

<div>

## EXAMPLE 3

In Example 3, all the device update configuration settings that have been configured at the site scope are removed. To do this, the **Get-CsDeviceUpdateConfiguration** cmdlet and the Filter parameter are used to return all the settings that have an Identity that begins with the string value "site:"; by definition, these will all be settings that were configured at the site scope. That collection is then piped to the **Remove-CsDeviceUpdateConfiguration** cmdlet, which removes each of the items in the collection.

    Get-CsDeviceUpdateConfiguration -Filter "site:*" | Remove-CsDeviceUpdateConfiguration 

</div>

<div>

## EXAMPLE 4

In Example 4, all the device update configuration settings that have a MaxLogFileSize property greater than 1024000 bytes are deleted. To accomplish this task, the **Get-CsDeviceUpdateConfiguration** cmdlet is first called in order to return a collection of all the device update configuration settings. This collection is piped to the **Where-Object** cmdlet, which selects only those configuration settings where the MaxLogFileSize property is greater than 1024000 bytes. That filtered collection is then piped to the **Remove-CsDeviceUpdateConfiguration** cmdlet, which deletes each item in the collection.

    Get-CsDeviceUpdateConfiguration | Where-Object {$_.MaxLogFileSize -lt 1024000} | Remove-CsDeviceUpdateConfiguration

</div>

</div>

<div>

## Detailed Description

The Device Update Web service provides a way for administrators to distribute firmware updates to devices that run Lync Phone Edition. Periodically, administrators upload a set of device update rules to Lync Server. After those rules have been tested and approved, they can then be applied to the appropriate devices as those devices connect to the system. Devices check for updates when they are first powered on, then check again when a user logs on. After that, devices check for updates every 24 hours.

Lync Server uses device update configuration settings to manage the Device Update Web service; these configuration settings can be applied at the global scope or at the site scope. By default, settings are found only at the global scope; however, you can use the **New-CsDeviceUpdateConfiguration** cmdlet to assign customized settings at the site scope as well.

In addition, you can use the **Remove-CsDeviceUpdateConfiguration** cmdlet to delete settings that have been assigned at the site scope. When you run this cmdlet against a site, the device update configuration settings assigned to that site are removed. You can also run the **Remove-CsDeviceUpdateConfiguration** cmdlet against the global settings. In that case, however, the global settings will not be removed; that’s because you cannot remove the global device update configuration settings. Instead, the global properties will be reset to their default values. For example, suppose you have changed the global property MaxLogCacheLimit to 1,024,000 bytes. If you run the **Remove-CsDeviceUpdateConfiguration** cmdlet against the global settings, the global settings will not be removed; however, any properties that have been modified will be reset to their default values. That means that MaxLogCacheLimit will be reset to 512,000 bytes.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsDeviceUpdateConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsDeviceUpdateConfiguration"}

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
<td><p>Indicates the Identity of the device update configuration settings to be removed. To refer to the global settings, use this syntax: -Identity global. To refer to site settings, use syntax similar to this: -Identity site:Redmond. Note that you cannot use wildcards when specifying an Identity.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.DeviceUpdateConfiguration object. The **Remove-CsDeviceUpdateConfiguration** cmdlet accepts pipelined instances of the device update configuration object.

</div>

<div>

## Return Types

None. Instead, the **Remove-CsDeviceUpdateConfiguration** cmdlet deletes instances of the Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.DeviceUpdateConfiguration object.

</div>

<div>

## See Also


[Get-CsDeviceUpdateConfiguration](get-csdeviceupdateconfiguration.md)  
[New-CsDeviceUpdateConfiguration](new-csdeviceupdateconfiguration.md)  
[Set-CsDeviceUpdateConfiguration](set-csdeviceupdateconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

