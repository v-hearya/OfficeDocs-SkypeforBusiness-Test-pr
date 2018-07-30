---
title: Get-CsConfigurationStoreLocation
TOCTitle: Get-CsConfigurationStoreLocation
ms:assetid: abfda147-02fa-46a5-a988-d83daf4cc455
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412814(v=OCS.15)
ms:contentKeyID: 48185115
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsConfigurationStoreLocation

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Reports back the location of the Active Directory service control point for the Central Management store. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsConfigurationStoreLocation [-GlobalSettingsDomainController <Fqdn>] [-Report <String>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 returns the SQL Server path to the computer (or pool) hosting the Central Management store.

    Get-CsConfigurationStoreLocation

</div>

<div>

## EXAMPLE 2

Example 2 is a variation of the command shown in Example 1; in this case, however, the Report parameter is included in order to specify a path for the report generated when you run the **Get-CsConfigurationStoreLocation** cmdlet.

    Get-CsConfigurationStoreLocation -Report "C:\Logs\ConfigurationStore.html"

</div>

</div>

<div>

## Detailed Description

Active Directory Domain Services uses service control points (SCP) to help computers locate services. For example, when you install Lync Server, a service control point is created that provides location information for the Central Management store used to maintain Lync Server data. Computers that need access to the database connect to Active Directory and use the information contained in the SCP to help them locate the correct computer and the correct instance of SQL Server.

The **Get-CsConfigurationStoreLocation** cmdlet is used to report back the SQL Server path (for example, atl-sql-001.litwareinc.com/rtc) to the computer running the Central Management store.

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
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Get-CsConfigurationStoreLocation** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

String. The **Get-CsConfigurationStoreLocation** cmdlet reports back the location of the configuration store.

</div>

<div>

## See Also


[Remove-CsConfigurationStoreLocation](remove-csconfigurationstorelocation.md)  
[Set-CsConfigurationStoreLocation](set-csconfigurationstorelocation.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

