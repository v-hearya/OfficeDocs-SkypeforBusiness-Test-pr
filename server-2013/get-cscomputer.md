---
title: Get-CsComputer
TOCTitle: Get-CsComputer
ms:assetid: 493931a9-1670-4a76-abba-7d3c7723d2e1
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425959(v=OCS.15)
ms:contentKeyID: 48184006
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsComputer

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Returns information about the computers that perform service roles within your Lync Server infrastructure. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsComputer [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsComputer [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Local <SwitchParameter>] [-Pool <String>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

In Example 1 the **Get-CsComputer** cmdlet is used to return information about all the computers that perform service roles within your Lync Server infrastructure.

    Get-CsComputer

</div>

<div>

## EXAMPLE 2

The command shown in Example 2 uses the Filter parameter to return only those service role computers that are part of the litwareinc.com domain. The wildcard string \*.litwareinc.com restricts the returned information to computers that have an FQDN that ends with the string value ".litwareinc.com".

    Get-CsComputer -Filter "*.litwareinc.com"

</div>

<div>

## EXAMPLE 3

In Example 3, the Identity parameter is used to limit the returned data to the one computer that has the FQDN atl-cs-001.litwareinc.com.

    Get-CsComputer -Identity "atl-cs-001.litwareinc.com"

</div>

<div>

## EXAMPLE 4

In Example 4, the Pool parameter is used to return information about all the computers found in the pool atl-cs-001.litwareinc.com.

    Get-CsComputer -Pool "atl-cs-001.litwareinc.com"

</div>

</div>

<div>

## Detailed Description

The **Get-CsComputer** cmdlet provides a way to quickly identify computers that are running Lync Server services or server roles. Called without any parameters, the **Get-CsComputer** cmdlet returns a collection of all the computers that are running Lync Server services or server roles; this collection includes the Identity, pool name, and fully qualified domain name (FQDN) for each computer. Alternatively, you can use optional parameters such as Identity, Filter, or Pool to limit the returned data to a single computer or set of computers.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsComputer** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins, RTCUniversalReadOnlyAdmins.

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
<td><p>Enables you to use wildcard characters when specifying the Identity of the computer (or computers) to be returned. For example, this command returns information about all the computers that have an Identity that begins with the string value &quot;atl-&quot;: -Filter &quot;atl-*&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>FQDN of the computer to be returned. For example: -Identity &quot;atl-cs-001.litwareinc.com&quot;.</p>
<p>If this parameter is not specified, all of the computers running Lync Server will be returned.</p></td>
</tr>
<tr class="odd">
<td><p><em>Local</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>When present, returns information only for the local computer.</p></td>
</tr>
<tr class="even">
<td><p><em>Pool</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>FQDN of a Lync Server pool. When you use this parameter, information about all the computers in the specified pool will be returned.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Get-CsComputer** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Get-CsComputer** cmdlet returns instances of the Microsoft.Rtc.Management.Deploy.Internal.Machine object.

</div>

<div>

## See Also


[Disable-CsComputer](disable-cscomputer.md)  
[Enable-CsComputer](enable-cscomputer.md)  
[Test-CsComputer](test-cscomputer.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

