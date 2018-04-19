---
title: Get-CsTenantLicensingConfiguration
TOCTitle: Get-CsTenantLicensingConfiguration
ms:assetid: 0df23143-f1aa-4850-b0f7-750422762925
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362770(v=OCS.15)
ms:contentKeyID: 56280892
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsTenantLicensingConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-05-09_

Indicates whether licensing information for the specified tenant is available in the Lync admin center.

This cmdlet can only be used with Lync Online.

<div>

## Syntax

    Get-CsTenantLicensingConfiguration [-Filter] <Object>] [-Identity] <Object>] [-Tenant] <Object>] [-LocalStore]

</div>

<div>

## Detailed Description

The Get-CsTenantLicensingConfiguration cmdlet indicates whether licensing information for the specified tenant is available in the Lync admin center. The cmdlet returns information similar to this:

Identity : Global  
Status : Enabled

If the Status is equal to Enabled then licensing information is available in the Lync admin center. If not, then licensing information is not available in the Lync admin center.

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
<td><p><strong>Filter</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to use wildcard characters in order to return a collection of tenant licensing configuration settings. Because each tenant is limited to a single, global collection of licensing configuration settings there is no need to use the Filter parameter.</p></td>
</tr>
<tr class="even">
<td><p><strong>Identity</strong></p></td>
<td><p>Optinal</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Specifies the collection of tenant licensing configuration settings to be returned. Because each tenant is limited to a single, global collection of licensing settings there is no need include this parameter when calling the Get-CsTenantLicensingConfiguration cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><strong>LocalStore</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the tenant licensing configuration data from the local replica of the Central Management store, rather than the Central Management store itself.</p></td>
</tr>
<tr class="even">
<td><p><strong>Tenant</strong></p></td>
<td><p>Optional</p></td>
<td><p>System.Guid</p></td>
<td><p>Globally unique identifier (GUID) of the tenant account whose licensing settings are being returned. For example:</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>You can return the tenant ID for each of your tenants by running this command:</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

The Get-CsTenantLicensingConfiguration cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The Get-CsTenantLicensingConfiguration cmdlet returns instances of the Deserialized.Microsoft.Rtc.Management.WritableConfig.Settings.TenantConfiguration.TenantLicensingConfiguration object.

</div>

<div>

## Example

The command shown in Example 1 returns licensing configuration information for the current tenant:

    Get-CsTenantLicensingConfiguration

</div>

</div>

<span> </span>

</div>

</div>

</div>

