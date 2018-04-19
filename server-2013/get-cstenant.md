---
title: Get-CsTenant
TOCTitle: Get-CsTenant
ms:assetid: 7b642117-5ca7-4a5b-bca7-16b0ae694ae2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ994044(v=OCS.15)
ms:contentKeyID: 51803955
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsTenant

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Returns information about the Lync Online tenants that have been configured for use in your organization. Tenants represent groups of online users. In many cases, you might need only a single tenant. However, if different groups of users have different management needs, Lync Online provides support for a single organization having multiple tenants.

Get-CsTenant can only be used with Lync Online.

<div>

## Syntax

    Get-CsTenant [[-Identity] <OUIdParameter>] [-Filter <String>] [-ResultSize <Unlimited`1>] [-Verbose]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 returns information about all the tenants configured for use in the organization.

    Get-CsTenant

</div>

<div>

## Example 2

In Example 2, information is returned for a single tenant: the tenant with the Identity "bf19b7db-6960-41e5-a139-2aa373474354".

    Get-CsTenant -Identity "bf19b7db-6960-41e5-a139-2aa373474354"

</div>

<div>

## Example 3

The preceding command shows an alternate way to return information for a single tenant; in this example, that's done by including the Filter parameter and the filter value {DisplayName –eq "Fabrikam"}. That syntax returns information only for the tenant that has the display name Fabrikam.

    Get-CsTenant -Filter {DisplayName -eq "Fabrikam"}

</div>

<div>

## Example 4

The command shown in Example 4 returns information for all the tenants that have a ServiceInstance equal to "LitwareincCommunicationsOnline/San Antonio". To do this, the command includes the Filter parameter and the filter value {ServiceInstance -eq "LitwareincCommunicationsOnline/San Antonio"}. That filter value limits returned data to tenants that have a ServiceInstance property equal to (-eq) "LitwareincCommunicationsOnline/San Antonio".

    Get-CsTenant -Filter {ServiceInstance -eq "LitwareincCommunicationsOnline/San Antonio"}

</div>

<div>

## Example 5

Example 5 returns information for all tenants that have a country or region display name equal to Australia. This is done by using the Filter parameter and the parameter value {CountryOrRegionDisplayName -eq "Australia"}.

    Get-CsTenant -Filter {CountryOrRegionDisplayName -eq "Australia"}

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

In Lync Online, tenants represents groups of users who have accounts homed on the service. Many organizations will require only a single tenant in which to house all their user accounts. However, Lync Online management is often performed on a tenant-by-tenant basis; that means that all the users in the same tenant will have the same voice policy, the same federation configuration settings, and so on. If you need to manage some users in one way and other users in another way, you might consider using multiple tenants, each with its own collection of policies and settings.

Regardless of the number of tenants you have, you can return information about these tenants by using the **Get-CsTenant** cmdlet.

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
<td><p>Enables you to return data by using Active Directory attributes and without having to specify the full Active Directory distinguished name. For example, to retrieve a tenant by using the tenant display name, use syntax similar to this:</p>
<p>Get-CsTenant –Filter {DisplayName –eq &quot;FabrikamTenant&quot;}</p>
<p>To return all tenants that use a Fabrikam domain use this syntax:</p>
<p>Get-CsTenant –Filter {Domains –like &quot;*fabrikam*&quot;}</p>
<p>The Filter parameter uses the same Windows PowerShell filtering syntax is used by the Where-Object cmdlet.</p>
<p>You cannot use both the Identity parameter and the Filter parameter in the same command.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.AD.OUIdParameter</p></td>
<td><p>Active Directory distinguished name of the tenant. For example:</p>
<p>-Identity &quot;OU=bf19b7db-6960-41e5-a139-2aa373474354,OU=OCS Tenants,dc=litwareinc,dc=com&quot;</p>
<p>If you do not include either the Identity or the Filter parameter then the <strong>Get-CsTenant</strong> cmdlet will return information about all your tenants.</p></td>
</tr>
<tr class="odd">
<td><p><em>ResultSize</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.Unlimited`1</p></td>
<td><p>Enables you to limit the number of records returned by the cmdlet. For example, to return seven tenants (regardless of the number of tenants that are in your forest) include the ResultSize parameter and set the parameter value to 7. Note that there is no way to guarantee which 7 users will be returned.</p>
<p>The result size can be set to any whole number between 0 and 2147483647, inclusive. If set to 0 the command will run, but no data will be returned. If you set the tenants to 7 but you have only three contacts in your forest, the command will return those three tenants and then complete without error.</p></td>
</tr>
</tbody>
</table>


</div>

<span id="InputTypes"></span>

<div>

## Input Types

The **Get-CsTenant** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.ADConnect.Schema.TenantObject object as well as string values representing the Identity of a Lync Online tenant (for example "OU=bf19b7db-6960-41e5-a139-2aa373474354,OU=OCS Tenants,dc=vdomain,dc=com").

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **Get-CsTenant** cmdlet returns instances of the Microsoft.Rtc.Management.ADConnect.Schema.TenantObject object.

</div>

<div>

## See Also


[Get-CsOnlineUser](get-csonlineuser.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

