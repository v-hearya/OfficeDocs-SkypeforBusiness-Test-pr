---
title: Set-CsTenantHybridConfiguration
TOCTitle: Set-CsTenantHybridConfiguration
ms:assetid: 805ac9ee-df40-40e1-baaa-adffb6bd8cf6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ994046(v=OCS.15)
ms:contentKeyID: 51803957
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsTenantHybridConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-08-13_

Used in a hybrid scenario to give users homed on Microsoft Lync Online access to on-premises Enterprise Voice features such as media bypass, Enhanced 9-1-1, and call parking. A hybrid scenario (also known as a split-domain scenario) is a Lync Server deployment in which some users have accounts homed on-premises while other users have accounts homed on Lync Online.

This cmdlet can only be used with Lync Online.

<div>

## Syntax

    Set-CsTenantHybridConfiguration [[-Identity] <XdsIdentity>] [-Tenant <guid>] [-PeerDestination <string>] [-HybridConfigServiceInternalUrl <string>] [-HybridConfigServiceExternalUrl <string>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]Set-CsTenantHybridConfiguration [-Tenant <guid>] [-PeerDestination <string>][-HybridConfigServiceInternalUrl <string>] [-HybridConfigServiceExternalUrl <string>] [-Instance <psobject>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 sets the internal service URL for the global collection of tenant hybrid configuration settings. To configure a global setting, include the Identity parameter along with the parameter value "global".

    Set-CsTenantHybridConfiguration -Identity "global" - HybridConfigServiceInternalUrl "https://internal.litwareinc.com"

</div>

<div>

## Example 2

In Example 2, the internal service URL is configured for a specific tenant; in this example, the tenant that has the TenantID "bf19b7db-6960-41e5-a139-2aa373474354". When a property value is explicitly assigned to an individual tenant, the tenant will be governed by their individual tenant hybrid configuration settings instead of the global settings.

    Set-CsTenantHybridConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" HybridConfigServiceInternalUrl "https://internal.litwareinc.com"

</div>

<div>

## Example 3

The command shown in Example 3 configures the internal service URL for all of your organization's tenants. To do this, the command first uses the **Get-CsTenant** cmdlet to return a collection of all the available tenants; that collection is then piped to the **ForEach-Object** cmdlet. In turn, the **ForEach-Object** cmdlet runs the **Set-CsTenantHybridConfiguration** cmdlet against each tenant in the collection, setting the internal service URL for each of those tenants to "https://internal.litwareinc.com".

    Get-CsTenant | ForEach-Object {Set-CsTenantHybridConfiguration -Tenant $_.TenantID -HybridConfigServiceInternalUrl "https://internal.litwareinc.com"}

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

In a hybrid or "split domain" deployment, an organization has some users who have accounts homed on Lync Online while simultaneously having other users who have accounts homed on Lync Server. By default, users homed on Lync Online do not have access to the complete range of capabilities offered by Enterprise Voice; that's because the Lync Online servers do not have direct access to on-premises Lync Server deployment and network configuration information. Among other things, Lync Online users do not have default access to such things as:

  - Enhanced 9-1-1, the Lync Server service used for making emergency phone calls.

  - Call parking, the Lync Server service which enables users to place a call on hold phone A, then retrieve that call from phone B.

  - Media bypass, which enables calls to and from the public switched telephone network (PSTN) to bypass the Mediation server, helping to minimize transcoding and network latency.

  - PSTN conferencing dial-in and dial-out, which enables users to participate in the audio portion of an online conference by using any PSTN telephone or mobile device.

  - The Response Group application, which provides a way for you to automatically route phone calls to entities such as a help desk or customer support line. By default, Lync Online users cannot function as Response Group agents.

In order to provide Lync Online users with access to these Enterprise Voice capabilities, administrators need to assign the appropriate values to hybrid configuration settings such as the internal and external Web service URLs and the fully qualified domain name of the organization's Access Edge server. These values, which can only be configured by using the **Set-CsTenantHybridConfiguration** cmdlet, provide the Lync Online servers with the information needed to make use of these advanced Enterprise Voice features.

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
<td></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might arise when running the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>HybridConfigServiceExternalUrl</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>External Web service URL.</p></td>
</tr>
<tr class="even">
<td><p><em>HybridConfigServiceInternalUrl</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Internal Web service URL.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Unique Identity of the tenant hybrid configuration settings to be modified. Because you are limited to a single, global collection of hybrid configuration settings, the only collection that can be modified by using the Identity parameter is the global collection:</p>
<p>-Identity global</p>
<p>To modify the settings for an individual tenant, use the Tenant parameter instead of the Identity parameter.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.PSObject</p></td>
<td><p>Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.</p></td>
</tr>
<tr class="odd">
<td><p><em>PeerDestination</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Fully qualified domain name of your on-premises Access Edge server.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Guid</p></td>
<td><p>Globally unique identifier (GUID) of the tenant account whose hybrid configuration settings are being modified. For example:</p>
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

None. The **Set-CsTenantHybridConfiguration** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

None. Instead, the **Set-CsTenantHybridConfiguration** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.HybridConfiguration.TenantHybridConfiguration object.

</div>

<div>

## See Also


[Get-CsTenantHybridConfiguration](get-cstenanthybridconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

