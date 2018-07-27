---
title: Get-CsNetworkInterface
TOCTitle: Get-CsNetworkInterface
ms:assetid: 06a5fedf-d87e-4469-9bd6-ad16c1f9a801
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398121(v=OCS.15)
ms:contentKeyID: 48183301
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsNetworkInterface

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Returns information about the network interfaces in use on computers running Lync Server services or server roles. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsNetworkInterface [-Identity <NetworkInterfaceIdentity>] <COMMON PARAMETERS>

    Get-CsNetworkInterface [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-ComputerFqdn <Fqdn>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 returns information for all the network interfaces configured for use in the organization.

    Get-CsNetworkInterface

</div>

<div>

## EXAMPLE 2

The command shown in Example 2 returns information about a single network interface: the interface that has the Identity atl-cs-001.litwareinc.com.com/Primary/1.

    Get-CsNetworkInterface -Identity atl-cs-001.litwareinc.com/Primary/1

</div>

<div>

## EXAMPLE 3

In Example 3, information is returned for all the network interfaces in the domain litwareinc.com. To do this, the Filter parameter is included, along with the filter value "\*.litwareinc.com\*". This filter value limits the returned data to interfaces that have an Identity that includes the string value "litwareinc.com".

    Get-CsNetworkInterface -Filter "*.litwareinc.com*"

</div>

<div>

## EXAMPLE 4

Example 4 returns information about all the network interfaces configured for the IP address 192.168.0.240. To do this, the command first calls the **Get-CsNetworkInterface** cmdlet without any parameters; this returns a collection of all the network interfaces configured for use in the organization. That collection is then piped to the **Where-Object** cmdlet, which picks out only those interfaces where the IPAddress property is equal to 192.168.0.240.

    Get-CsNetworkInterface | Where-Object {$_.IPAddress -eq "192.168.0.240"}

</div>

<div>

## EXAMPLE 5

The command shown in Example 5 is a variation of the command shown in Example 4; in this case, however, information is returned for all the network interfaces configured for the subnet "192.168.0.\*". This is done by retrieving a collection of all the network interfaces, piping that collection to the **Where-Object** cmdlet, and then picking out only those interfaces where IPAddress starts with the string value "192.168.0.".

    Get-CsNetworkInterface | Where-Object {$_.IPAddress -like "192.168.0.*"}

</div>

<div>

## EXAMPLE 6

Example 6 returns all the network interfaces that have been configured for external access. To do this, the **Get-CsNetworkInterface** cmdlet is first called without any parameters; this returns a collection of all the network interfaces currently in use. This collection is then piped to the **Where-Object** cmdlet, which selects only those items where the Interface property is equal to External.

    Get-CsNetworkInterface | Where-Object {$_.Interface -eq "External"}

</div>

</div>

<div>

## Detailed Description

In order for information to be transmitted from one computer to another, computers need network interfaces: connections between a computer and the network. Computers running Lync Server services or server roles must have at least one network interface; otherwise they will not be able to communicate with other computers. However, these computers can also have multiple network interfaces; for example, an Edge Server might have one interface for connecting to the internal network and a second interface for connecting to the Internet. The **Get-CsNetworkInterface** cmdlet provides a way for administrators to return information about the network interfaces currently in use on computers running Lync Server services or server roles.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsNetworkInterface** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsNetworkInterface"}

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
<td><p><em>ComputerFqdn</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>FQDN of the computer for which network interface information is to be returned. For example, to return network interface information for the computer atl-cs-001.litwareinc.com (and only for that computer) use this syntax: -ComputerFqdn atl-cs-001.litwareinc.com.</p></td>
</tr>
<tr class="even">
<td><p><em>Filter</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to use wildcards when specifying the network interface (or interfaces) to be returned. For example, this syntax returns information about the Primary network interface used on all of your computers running a Lync Server service or server role: -Filter &quot;*/Primary/*&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.NetworkInterfaceIdentity</p></td>
<td><p>Unique identifier for the network interface to be returned. A network interface Identity consists of three parts:</p>
<p>The fully qualified domain name (FQDN) of the computer itself (for example, atl-cs-001.litwareinc.com).</p>
<p>The network interface &quot;side&quot; (Primary; Internal; External; public switched telephone network). The side indicates the type of traffic the port is used for.</p>
<p>The network interface number for that particular side.</p>
<p>For example: -Identity &quot;atl-cs-001.litwareinc.com/Primary/1&quot;.</p>
<p>The Identity, ComputerFqdn, and Filter parameters must be used separately; for example, you cannot run a command that uses both ComputerFqdn and Identity. In addition, you cannot use wildcard characters when specifying the Identity. To employ wildcards, use the Filter parameter.</p>
<p>If neither the Identity, ComputerFqdn, nor Filter parameters are used, then the <strong>Get-CsNetworkInterface</strong> cmdlet returns information about all the network interfaces currently in use on your computers running a Lync Server service or server role.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Get-CsNetworkInterface** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Get-CsNetworkInterface** cmdlet returns an instance of the Microsoft.Rtc.Management.Xds.DisplayNetworkInterface object.

</div>

<div>

## See Also


[Get-CsComputer](get-cscomputer.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

