---
title: Set-CsTenantFederationConfiguration
TOCTitle: Set-CsTenantFederationConfiguration
ms:assetid: e13c2f55-7a68-4174-a0da-5eec8c65f64c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ994080(v=OCS.15)
ms:contentKeyID: 51803991
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsTenantFederationConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-08-13_

Manages federation configuration settings for your Microsoft Lync Online tenants. These settings are used to determine which domains (if any) your users are allowed to communicate with.

The **Set-CsTenantFederationConfiguration** cmdlet can only be used with Lync Online.

<div>

## Syntax

    Set-CsTenantFederationConfiguration [[-Identity] <XdsIdentity>] [-Tenant <Nullable`1>] [-AllowedDomains <IAllowedDomainsChoice>] [-BlockedDomains <PSListModifier>] [-AllowFederatedUsers] [-AllowPublicUsers] [-SharedSipAddressSpace] [-Force] [-Verbose] [-WhatIf] [-Confirm]Set-CsTenantFederationConfiguration [-Tenant <Nullable`1>] [-AllowedDomains <IAllowedDomainsChoice>] [-BlockedDomains <PSListModifier>] [-AllowFederatedUsers] [-AllowPublicUsers] [-SharedSipAddressSpace] [-Instance <PSObject>] [-Force] [-Verbose] [-WhatIf] [-Confirm]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 disables communication with public providers for the tenant with the TenantId "bf19b7db-6960-41e5-a139-2aa373474354".

    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowPublicUsers $False

Note that the Tenant parameter is optional. If you leave off that parameter Windows PowerShell will automatically insert the correct Tenant ID based on your connection information.

</div>

<div>

## Example 2

Example 2 shows how you can disable public provider communication for all the tenants in your organization. To do this, the command first calls the **Get-CsTenant** cmdlet to return a collection of all the available tenants. That collection is then piped to the **Select-Object** cmdlet, which picks out only the TenantId property for each item in the collection. That collection of tenant IDs is then piped to the **ForEach-Object** cmdlet. The F**orEach-Object** cmdlet then takes each tenant ID and runs the **Set-CsTenantFederationConfiguration** cmdlet against that ID, setting the AllowPublicUsers property for each tenant to False ($False).

    Get-CsTenant | Select-Object TenantId | ForEach-Object {Set-CsTenantFederationConfiguration -Tenant $_.TenantId -AllowPublicUsers $False}

</div>

<div>

## Example 3

In Example 3, the domain fabrikam.com is assigned as the only domain on the blocked domains list for the tenant with the TenantId "bf19b7db-6960-41e5-a139-2aa373474354". To do this, the first command in the example uses the **New-CsEdgeDomainPattern** cmdlet to create a new domain object for fabrikam.com. This domain object is stored in a variable named $x.

The second command in the example then uses the **Set-CsTenantFederationConfiguration** cmdlet to update the blocked domains list. Using the Replace method ensures that the existing blocked domains list will be replaced by the new list: a list that contains only the domain fabrikam.com.

    $x = New-CsEdgeDomainPattern "fabrikam.com"
    Set-CsTenantFederationConfiguration -Tenant bf19b7db-6960-41e5-a139-2aa373474354 -BlockedDomains @{Replace=$x}

</div>

<div>

## Example 4

The commands shown in Example 4 remove fabrikam.com from the list of domains blocked by the tenant with the TenantID "bf19b7db-6960-41e5-a139-2aa373474354". To do this, the first command in the example uses the **New-CsEdgeDomainPattern** cmdlet to create a domain object for fabrikam.com. The resulting domain object is then stored in a variable named $x.

The second command in the example then uses the **Set-CsTenantFederationConfiguration** cmdlet and the Remove method to remove fabrikam.com from the blocked domains list for the specified tenant.

    $x = New-CsEdgeDomainPattern "fabrikam.com"
    Set-CsTenantFederationConfiguration -Tenant bf19b7db-6960-41e5-a139-2aa373474354 -BlockedDomains @{Remove=$x}

</div>

<div>

## Example 5

The commands shown in Example 5 add the domain fabrikam.com to the list of domains blocked by the tenant with the TenantId "bf19b7db-6960-41e5-a139-2aa373474354". To add a new blocked domain, the first command in the example uses the **New-CsEdgeDomainPattern** cmdlet to create a domain object for fabrikam.com. This object is stored in a variable named $x.

After the domain object has been created, the second command then uses the **Set-CsTenantFederationConfiguration** cmdlet and the Add method to add fabrikam.com to any domains already on the blocked domains list.

    $x = New-CsEdgeDomainPattern "fabrikam.com"
    Set-CsTenantFederationConfiguration -Tenant bf19b7db-6960-41e5-a139-2aa373474354 -BlockedDomains @{Add=$x}

</div>

<div>

## Example 6

Example 6 shows how you can remove all the domains assigned to the blocked domains list for a given tenant. To do this, simply include the BlockedDomains parameter, and set the parameter value to null ($Null). When this command completes, the blocked domain list will be cleared for the tenant with the TenantID "bf19b7db-6960-41e5-a139-2aa373474354".

    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -BlockedDomains $Null

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

Federation is a service that enables users to exchange IM and presence information with users from other domains. With Lync Online, administrators can use the federation configuration settings to govern:

  - <span></span>  
    Whether or not users can communicate with people from other domains and, if so, which domains they are allowed to communicate with.

  - <span></span>  
    Whether or not users can communicate with people who have accounts on public IM and presence providers such as Windows Live, AOL, and Yahoo.

Administrators can use the **Set-CsTenantFederationConfiguration** cmdlet to enable and disable federation with other domains and federation with public providers. In addition, this cmdlet can be used to expressly indicate the domains that users can communicate with and/or the domains that users are not allowed to communicate with. However, administrators must use the **Set-CsTenantPublicProvider** cmdlet in order to indicate the public IM and presence providers that users can and cannot communicate with.

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
<td><p><em>AllowedDomains</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.Edge.IAllowedDomainsChoice</p></td>
<td><p>Domain objects (created by using the <strong>New-CsEdgeAllowList</strong> cmdlet or the <strong>New-CsEdgeAllowAllKnownDomains</strong> cmdlet) that represent the domains that users are allowed to communicate with. If the <strong>New-CsEdgeAllowAllKnownDomains</strong> cmdlet is used then users can communicate with any domain that does not appear on the blocked domains list. If the <strong>New-CsEdgeAllowList</strong> cmdlet is used then users can only communicate with domains that have been added to the allowed domains list.</p>
<p>Note that string values cannot be passed directly to the AllowedDomains parameter. Instead, you must create an object reference using the <strong>New-CsEdgeAllowList</strong> cmdlet or the <strong>New-CsEdgeAllowAllKnownDomains</strong> cmdlet and then use the object reference variable as the parameter value.</p></td>
</tr>
<tr class="even">
<td><p><em>AllowFederatedUsers</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>When set to True (the default value) users will be potentially allowed to communicate with users from other domains. If this property is set to False then users cannot communicate with users from other domains regardless of the values assigned to the AllowedDomains and BlockedDomains properties.</p></td>
</tr>
<tr class="odd">
<td><p><em>AllowPublicUsers</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>When set to True (the default value) users will be potentially allowed to communicate with users who have accounts on public IM and presence providers such as Windows Live, Yahoo, and AOL. The collection of public providers that users can actually communicate with is managed by using the Set-CsTenantPublicProvider cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>BlockedDomains</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>If the AllowedDomains property has been set to AllowAllKnownDomains, then users will be allowed to communicate with users from any domain except domains that appear in the blocked domains list. If the AllowedDomains property has not been set to AllowAllKnownDomains, then the blocked list is ignored, and users can only communicate with domains that have been expressly added to the allowed domains list.</p></td>
</tr>
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
<td><p>Suppresses the display of any non-fatal error message that might arise when running the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Specifies the collection of tenant federation configuration settings to be modified. Because each tenant is limited to a single, global collection of federation settings there is no need include this parameter when calling the <strong>Set-CsTenantFederationConfiguration</strong> cmdlet. If you do choose to use the Identity parameter you must also include the Tenant parameter. For example:</p>
<p>Set-CsTenantFederationConfiguration -Tenant &quot;bf19b7db-6960-41e5-a139-2aa373474354&quot; –Identity &quot;global&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.PSObject</p></td>
<td><p>Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.</p></td>
</tr>
<tr class="odd">
<td><p><em>SharedSipAddressSpace</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>When set to True, indicates that the users homed on Lync Online use the same SIP domain as users homed on the on-premises version of Lync Server. The default value is False, meaning that the two sets of users gave have different SIP domains.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Guid</p></td>
<td><p>Globally unique identifier (GUID) of the tenant account whose federation settings are being modified. For example:</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>You can return the tenant ID for each of your tenants by running this command:</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p>
<p>If you are using a remote session of Windows PowerShell and are connected only to Lync Online you do not have to include the Tenant parameter. Instead, the tenant ID will automatically be filled in for you based on your connection information. The Tenant parameter is primarily for use in a hybrid deployment.</p></td>
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

<span id="InputTypes"></span>

<div>

## Input Types

The **Set-CsTenantFederationConfiguration** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.TenantFederationSettings object.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

None. Instead, the **Set-CsTenantFederationConfiguration** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.TenantFederationSettings object.

</div>

<div>

## See Also


[Get-CsTenantFederationConfiguration](get-cstenantfederationconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

