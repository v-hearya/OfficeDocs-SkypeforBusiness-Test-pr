---
title: Remove-CsConfigurationStoreLocation
TOCTitle: Remove-CsConfigurationStoreLocation
ms:assetid: 141be225-c6e4-4377-913b-ba61528929d4
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398214(v=OCS.15)
ms:contentKeyID: 48183475
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsConfigurationStoreLocation

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Removes the Active Directory service control point for the Central Management store. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsConfigurationStoreLocation [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-GlobalSettingsDomainController <Fqdn>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 removes the Active Directory service control point for the Central Management store. To restore this SCP (or to create a new SCP), you must run the **Set-CsConfigurationStoreLocation** cmdlet.

    Remove-CsConfigurationStoreLocation

</div>

<div>

## EXAMPLE 2

Example 2 also removes the Active Directory service control point for the Central Management store. In addition to deleting the SCP, this command records information about the success (or failure) of the operation to the log file C:\\Logs\\Store\_Location.html. To create this log file, the command uses the Report parameter followed by the path to the log file where information should be recorded. If this file already exists, the contents will be overwritten when the command runs. If the file does not exist, it will be created when the command runs.

    Remove-CsConfigurationStoreLocation -Report C:\Logs\Store_Location.html

</div>

</div>

<div>

## Detailed Description

Active Directory Domain Services uses service control points (SCP) to help computers locate services. For example, when you install Lync Server, an SCP is created that provides location information for the Central Management store used to maintain Lync Server data. Computers that need access to the database connect to Active Directory and use the information contained in the SCP to help them locate the correct computer and the correct instance of SQL Server.

As noted, when you install Lync Server, an SCP for the Central Management store is automatically created for you. Typically, you do not want to delete that SCP; if you do, computers will not be able to locate the database. However, there might be times (perhaps when troubleshooting a problem) when you will need to delete the SCP. To do that, use the **Remove-CsConfigurationStoreLocation** cmdlet. After the SCP has been deleted, you can recreate it (or create a new service control point) by using the **Set-CsConfigurationStoreLocation** cmdlet.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsConfigurationStoreLocation** cmdlet: RTCUniversalServerAdmins.

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
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>GlobalSettingsDomainController</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Fully qualified domain name (FQDN) of a domain controller where global settings are stored. If global settings are stored in the Active Directory System container, then this parameter must point to the root domain controller. If global settings are stored in the Configuration container, then any domain controller can be used and this parameter can be omitted.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report &quot;C:\Logs\ConfigurationStore.html&quot;</p></td>
</tr>
<tr class="odd">
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

None. The **Remove-CsConfigurationStoreLocation** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Remove-CsConfigurationStoreLocation** cmdlet does not return any objects or values.

</div>

<div>

## See Also


[Get-CsConfigurationStoreLocation](get-csconfigurationstorelocation.md)  
[Set-CsConfigurationStoreLocation](set-csconfigurationstorelocation.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

