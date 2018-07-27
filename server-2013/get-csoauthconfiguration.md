---
title: Get-CsOAuthConfiguration
TOCTitle: Get-CsOAuthConfiguration
ms:assetid: a3fda8bf-84e3-4d14-a1c5-093e6eb36ffe
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205155(v=OCS.15)
ms:contentKeyID: 48185054
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsOAuthConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Returns information about the Open Authorization (OAuth) configuration settings currently in use in the organization. OAuth is a standard protocol used for server-to-server authentication and authorization. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Get-CsOAuthConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsOAuthConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>] [-Tenant <Guid>]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 returns information for the OAuth configuration settings in use in the organization.

    Get-CsOAuthConfiguration

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

In Lync Server 2013, server-to-server authentication (for example, the authentication that enables Lync Server and Microsoft Exchange Server 2013 to share information) is carried out using the OAuth security protocol. OAuth is always on in Lync Server 2013; there is no need (or even any way) to enable or disable the protocol. However, if Lync Server needs to communicate with other server products (such as Exchange 2013 or Microsoft SharePoint 2013) you might need to modify your OAuth configuration settings; for example, you might need to specify the autodiscover URL for the Office 365 version of Exchange, and you might need to specify your Realm name. These settings can only be managed by using the **CsOAuthConfiguration** cmdlets; options for managing OAuth settings are not available in the Lync Server 2013 Control Panel.

Note that, for the on-premises version of Lync Server 2013, you can have only a single, global collection of OAuth settings: you cannot not create additional collections of OAuth settings nor can you delete the global collection. Each Lync Online tenant is also limited to a single collection of OAuth configuration settings.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsOAuthConfiguration"}

**Lync Server Control Panel:** The functions carried out by the **Get-CsOAuthConfiguration** cmdlet are not available in the Lync Server Control Panel.

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
<td><p>Enables you to use wildcard values when referencing a collection of OAuth configuration settings. Because you can only have a single, global instance of these settings there is no reason to use the Filter parameter. However, if you prefer you can use the following syntax to reference the global settings:</p>
<p>-Filter &quot;g*&quot;</p>
<p>That syntax brings back all the OAuth configuration settings that have an Identity that begins with the letter &quot;g&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Unique Identity of the OAuth configuration settings. Because you can only have a single, global instance of these settings, you do not need to specify an Identity when calling the <strong>Get-CsOAuthConfiguration</strong> cmdlet. If you prefer, however, you can use the following syntax to reference the global settings:</p>
<p>-Identity global</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the OAuth configuration data from the local replica of the Central Management store rather than from the Central Management store itself.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Guid</p></td>
<td><p>Globally unique identifier (GUID) of the Lync Online tenant account whose OAuth configuration settings are to be retrieved.</p>
<p>For example:</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>You can return the tenant ID for each of your tenants by running this command:</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
</tr>
</tbody>
</table>


</div>

<span id="InputTypes"></span>

<div>

## Input Types

None. The **Get-CsOAuthConfiguration** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **Get-CsOAuthConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SSAuth.OAuthSettings object.

</div>

<div>

## See Also


[Set-CsOAuthConfiguration](set-csoauthconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

