---
title: Set-CsTenantPublicProvider
TOCTitle: Set-CsTenantPublicProvider
ms:assetid: 8341d801-bfa1-4c5b-9b80-5d503deebaf7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ994047(v=OCS.15)
ms:contentKeyID: 51803958
ms.date: 10/15/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsTenantPublicProvider

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-10-15_

Enables and disables communication with the third-party IM and presence providers Windows Live, AOL, and Yahoo. When enabled, Microsoft Lync Online users will be able to exchange IM and presence information with users who have accounts on the specified public provider.

The **Set-CsTenantPublicProvider** cmdlet can only be used with Lync Online.

<div>

## Syntax

    Set-CsTenantPublicProvider -Tenant <String> [-Provider <String[]>] [-Verbose] [-WhatIf] [-Confirm]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 enables federation with Windows Live for the tenant with the tenant ID bf19b7db-6960-41e5-a139-2aa373474354. Because Windows Live is the only provider specified, both the AOL and Yahoo providers will be disabled after the command executes.

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "WindowsLive"

</div>

<div>

## Example 2

In Example 2, two public providers are enabled: Windows Live and AOL. That means that only the Yahoo public provider will be disabled for the specified tenant.

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "WindowsLive","AOL"

</div>

<div>

## Example 3

Example 3 shows how you can disable all the public providers for a given tenant. This is done by setting the Provider property to an empty string ("").

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider ""

</div>

<div>

## Example 4

The command shown in Example 4 disables all the public providers for all of your Lync Online tenants. To accomplish this task, the command first uses the **Get-CsTenant** cmdlet to return a collection of all of your tenants. This collection is then piped to the **ForEach-Object** cmdlet, which takes each tenant in the collection, calls the **Set-CsTenantPublicProvider** cmdlet against each of those tenants, and disables all the public providers. That last task is carried out by setting the Provider property to an empty string ("").

    Get-CsTenant | ForEach-Object {Set-CsTenantPublicProvider -Tenant $_.TenantId -Provider ""}

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

Public providers are organizations that provide SIP communication services for the general public. When you establish a federation relationship with a public provider, you effectively establish federation with any user who has an account hosted by that provider. For example, if you federate with Windows Live, then your users will be able to exchange instant messages and presence information with anyone who has a Windows Live instant messaging account.

Lync Online gives administrators the option of configuring federation with one or more of the following public IM and presence providers:

  - <span></span>  
    Windows Live

  - <span></span>  
    AOL

  - <span></span>  
    Yahoo\!

The **Set-CsTenantPublicProvider** cmdlet can be used to enable or disable federation with any of these public providers. When using this cmdlet, keep in mind that each time you run the **Set-CsTenantPublicProvider** cmdlet you must specify all of the providers that should be enabled. For example, suppose all three providers are disabled and you run this command:

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "WindowsLive"

As you might expect, that will enable Windows Live, and will leave AOL and Yahoo disabled.

Now, suppose you next run this command:

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "AOL"

That command will enable AOL. However, it will also disable Windows Live: that's because Windows Live was not specified as part of the parameter value supplied to the Provider parameter. If you want to enable AOL and keep Windows Live enabled as well, then you must specify both AOL and Windows Live when calling Set-CsTenantPublicProvider:

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "AOL","WindowsLive"

To disable federation for all three providers, set the Provider property to an empty string (""):

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider ""

Note that simply enabling the status of a public provider does not mean that users can exchange instant messages and presence information with users who have accounts on that provider. In addition to enabling federation with the provider itself, administrators must also set the AllowPublicUsers property of the federation configuration settings to True. If this property is set to False then communication will not be allowed with any of the public providers, regardless of the public provider configuration settings.

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
<td><p><em>Tenant</em></p></td>
<td><p>Required</p></td>
<td><p>System.Guid</p></td>
<td><p>Globally unique identifier (GUID) of the tenant account whose public provider settings are being modified. For example:</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>You can return the tenant ID for each of your tenants by running this command:</p>
<pre><code>Get-CsTenant | Select-Object DisplayName, TenantID</code></pre>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Provider</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String[]</p></td>
<td><p>Indicates the public provider (or providers) that users will be allowed to communicate with. Valid values are:</p>
<p>* AOL</p>
<p>* WindowsLive</p>
<p>* Yahoo</p>
<p>Note that, when configuring public providers, any provider included in the Provider parameter value will be enabled for use, while any provider not included in the parameter value will be disabled. For example, this syntax enables only Yahoo, while disabling Windows Live and AOL:</p>
<p>-Provider &quot;AOL&quot;</p>
<p>You can enable multiple providers by separating the provider names by using commas:</p>
<p>-Provider &quot;AOL&quot;,&quot;WindowsLive&quot;</p></td>
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

<span id="InputTypes"></span>

<div>

## Input Types

The **Set-CsTenantPublicProvider** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.Hosted.TenantPICStatus object.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

None. Instead, the **Set-CsTenantPublicProvider** cmdlet modifies existing instances of the Microsoft.Rtc.Management.Hosted.TenantPICStatus object.

</div>

<div>

## See Also


[Get-CsTenantPublicProvider](get-cstenantpublicprovider.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

