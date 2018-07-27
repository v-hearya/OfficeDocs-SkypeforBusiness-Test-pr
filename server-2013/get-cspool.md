---
title: Get-CsPool
TOCTitle: Get-CsPool
ms:assetid: e0911c68-9a0a-461a-88d6-c610c6cd996c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398992(v=OCS.15)
ms:contentKeyID: 48185683
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsPool

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-07_

Returns information about the pools used in your deployment of Lync Server. Pools are a collection of computers in a site that all run the same set of Lync Server services. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsPool [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsPool [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Site <String>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 returns all the pools found in your deployment of Lync Server.

    Get-CsPool

</div>

<div>

## EXAMPLE 2

Example 2 displays detailed information about the computers found in each of your pools. This is done by calling the **Get-CsPool** cmdlet, and then piping the returned data to the **Select-Object** cmdlet. The ExpandProperty parameter is then used to "expand" the value of the Computers property. The Computers property is an array of objects representing each computer in the pool. When you expand the Computers property you get back detailed information about each of these computers.

    Get-CsPool | Select-Object -ExpandProperty Computers

</div>

<div>

## EXAMPLE 3

In Example 3, the Identity parameter is used to restrict the returned data to the pool that has the Identity atl-cs-001.litwareinc.com.

    Get-CsPool -Identity atl-cs-001.litwareinc.com

</div>

<div>

## EXAMPLE 4

Example 4 returns all the pools found in the Redmond site. To do this, the command uses the Site parameter; the parameter value "Redmond" limits the returned data to pools where the Site property is equal to Redmond.

    Get-CsPool -Site "Redmond"

</div>

<div>

## EXAMPLE 5

The command shown in Example 5 returns a collection of all the pools that do not have any Lync Server services installed. To carry out this task, the command first calls the **Get-CsPool** cmdlet without any parameters; that returns a collection of all the pools currently in use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out all the pools where the Services.Count property is equal to 0. If the Count equals 0, that means that there are no Lync Server services configured for that pool.

    Get-CsPool | Where-Object {$_.Services.Count -eq 0}

</div>

</div>

<div>

## Detailed Description

In Lync Server, a pool is one or more computers in the same site that run the same set of services. For example, if you have one server running the Mediation Server service in the Redmond site, then you would have a Mediation Server pool consisting of that one computer. If you have two computers running Mediation Server in the Redmond site, then you would have a Mediation Server pool consisting of two computers. The number of pools used in your organization depends on the number of servers you have and the different services run by those servers.

The **Get-CsPool** cmdlet enables you to retrieve information about each pool in use in your organization, including information about the services running on each of those pools.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsPool** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins, RTCUniversalReadOnlyAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsPool"}

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
<td><p>Enables you to use wildcards when specifying the Identity of the pool (or pools) to be returned. For example, this syntax returns all the pools that have an Identity that ends with the string value &quot;.fabrikam.com&quot;: -Filter &quot;*.fabrikam.com&quot;.</p>
<p>Note that you cannot use both the Filter and the Identity parameters in the same command.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Fully qualified domain name (FQDN) of the pool to be returned. For example: -Identity atl-cs-001.litwareinc.com.</p>
<p>If this parameter is not present, then all the pools in your organization will be returned.</p></td>
</tr>
<tr class="odd">
<td><p><em>Site</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Returns all the pools found on the specified site. The site in question should be referenced using the site’s DisplayName (for example, Redmond) rather than the site Identity (for example, site:Redmond). For example: -Site &quot;Redmond&quot;. You can retrieve the display names for your sites by running this command:</p>
<p>Get-CsSite | Select-Object Identity, DisplayName</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Get-CsPool** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Get-CsPool** cmdlet returns instances of the Microsoft.Rtc.Management.Deploy.Internal.Cluster object.

</div>

<div>

## See Also


[Get-CsSite](get-cssite.md)  
[Get-CsTopology](get-cstopology.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

