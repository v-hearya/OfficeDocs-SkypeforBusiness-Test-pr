---
title: Get-CsTenantFederationConfiguration
TOCTitle: Get-CsTenantFederationConfiguration
ms:assetid: e5f836d0-6066-4c23-9594-6e3f1cbd39ef
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ994072(v=OCS.15)
ms:contentKeyID: 51803983
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsTenantFederationConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-08-13_

Returns information about the federation configuration settings for your Microsoft Lync Online tenants. Federation configuration settings are used to determine which domains (if any) your users are allowed to communicate with.

The **Get-CsTenantFederationConfiguration** cmdlet can only be used with Lync Online.

<div>

## Syntax

    Get-CsTenantFederationConfiguration [[-Identity] <XdsIdentity>] [-Tenant <Nullable`1>] [-LocalStore] [-Verbose] Get-CsTenantFederationConfiguration [-Tenant <Nullable`1>] [-Filter <String>] [-LocalStore] [-Verbose]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Exercise 1 returns federation configuration information for the tenant with the tenant ID "bf19b7db-6960-41e5-a139-2aa373474354". Tenant IDs can be retrieved using a command similar to this:

Get-CsTenant | Select-Object TenantID

    Get-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354"

Note that the Tenant parameter is optional. You can also call Get-CsTenantFederationConfiguration by using this syntax:

    Get-CsTenantFederationConfiguration

</div>

<div>

## Example 2

In Example 2, information is returned for all the domains found on the federation allowed list for the tenant bf19b7db-6960-41e5-a139-2aa373474354. (The allowed list represents all the domains that the tenant is allowed to federate with.) To do this, the command first calls the **Get-CsTenantFederationConfiguration** cmdlet to return federation information for the specified tenant. That information is then piped to the **Select-Object** cmdlet, which uses the ExpandProperty to "expand" the property AllowedList. Expanding a property simply means displaying all the information stored in that property onscreen, and in an easy-to-read format.

    Get-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" | Select-Object -ExpandProperty AllowedList

</div>

<div>

## Example 3

The preceding command returns federation configuration for all the tenants currently in use in the organization. To carry out this task, the command first calls the **Get-CsTenant** cmdlet without any parameters; that returns a collection of all the available tenants. That collection is then piped to the **ForEach-Object** cmdlet. ForEach-Object takes each tenant in the collection and calls the **Get-CsTenantFederationConfiguration** cmdlet, using the property value TenantID (returned by the **Get-CsTenant** cmdlet) to represent the tenant ID.

    Get-CsTenant | ForEach-Object {Get-CsTenantFederationConfiguration -Tenant $_.TenantId}

</div>

<div>

## Example 4

In Example 4, federation configuration information is only returned for tenants that do not allow federation with public users. To do this, the command first calls the **Get-CsTenant** cmdlet without any parameters in order to return a collection of all the tenants configured for use in the organization. That collection is piped to the **ForEach-Object** cmdlet, which takes each tenant in the collection and then uses the **Get-CsTenantFederationConfiguration** cmdlet to return federation configuration information. The entire set of federation configuration information is then piped to the **Where-Object** cmdlet, which picks out only those tenants where the AllowPublicUsers property is equal to (-eq) $False.

    Get-CsTenant | Select-Object TenantId | ForEach-Object {Get-CsTenantFederationConfiguration -Tenant $_.TenantId} | Where-Object {$_.AllowPublicUsers -eq $False}

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

Federation is a service that enables users to exchange IM and presence information with users from other domains. With Lync Online, administrators can use the federation configuration settings to govern:

  - Whether or not users can communicate with people from other domains and, if so, which domains they are allowed to communicate with.

  - Whether or not users can communicate with people who have accounts on public IM and presence providers such as Windows Live, AOL, and Yahoo.

The **Get-CsTenantFederationConfiguration** cmdlet provides a way for administrators to return federation information for their Lync Online tenants. This cmdlet can also be used to review the allowed and blocked lists, lists which are used to specify domains that users can and cannot communicate with. However, administrators must use the **Get-CsTenantPublicProvider** cmdlet in order to see which public IM and presence providers users are allowed to communicate with.

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
<td><p>Enables you to use wildcard characters in order to return a collection of tenant federation configuration settings. Because each tenant is limited to a single, global collection of federation configuration settings there is no need to use the Filter parameter. However, this is valid syntax for the <strong>Get-CsTenantFederationConfiguration</strong> cmdlet:</p>
<p>Get-CsTenantFederationConfiguration –Tenant &quot;bf19b7db-6960-41e5-a139-2aa373474354&quot; –Filter &quot;g*&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Specifies the collection of tenant federation configuration settings to be returned. Because each tenant is limited to a single, global collection of federation settings there is no need include this parameter when calling the <strong>Get-CsTenantFederationConfiguration</strong> cmdlet. If you do choose to use the Identity parameter you must also include the Tenant parameter. For example:</p>
<p>Get-CsTenantFederationConfiguration -Tenant &quot;bf19b7db-6960-41e5-a139-2aa373474354&quot; –Identity &quot;global&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the tenant federation configuration data from the local replica of the Central Management store, rather than the Central Management store itself.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Guid</p></td>
<td><p>Globally unique identifier (GUID) of the tenant account whose federation settings are being returned. For example:</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>You can return the tenant ID for each of your tenants by running this command:</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p>
<p>If you are using a remote session of Windows PowerShell and are connected only to Lync Online you do not have to include the Tenant parameter. Instead, the tenant ID will automatically be filled in for you based on your connection information. The Tenant parameter is primarily for use in a hybrid deployment.</p></td>
</tr>
</tbody>
</table>


</div>

<span id="InputTypes"></span>

<div>

## Input Types

None. The **Get-CsTenantFederationConfiguration** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **Get-CsTenantFederationConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.TenantFederationSettings object.

</div>

<div>

## See Also


[Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

