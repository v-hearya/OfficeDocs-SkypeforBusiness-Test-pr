---
title: Set-CsEdgeServer
TOCTitle: Set-CsEdgeServer
ms:assetid: cbe140a4-8ce6-4e20-913b-b1ffb58e6698
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398859(v=OCS.15)
ms:contentKeyID: 48185500
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsEdgeServer

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-04_

Modifies the property values for one or more Edge Servers. Edge Servers are used to provide connectivity between your internal network and the Internet. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsEdgeServer [-Identity <XdsGlobalRelativeIdentity>] [-AccessEdgeClientSipPort <UInt16>] [-AccessEdgeExternalSipPort <UInt16>] [-AccessEdgeInternalSipPort <UInt16>] [-Confirm [<SwitchParameter>]] [-DataPsomClientPort <UInt16>] [-DataPsomServerPort <UInt16>] [-Force <SwitchParameter>] [-MediaCommunicationPortCount <UInt16>] [-MediaCommunicationPortStart <UInt16>] [-MediaRelayAuthEdgePort <UInt16>] [-MediaRelayExternalTurnTcpPort <UInt16>] [-MediaRelayExternalTurnUdpPort <UInt16>] [-MediaRelayInternalTurnTcpPort <UInt16>] [-MediaRelayInternalTurnUdpPort <UInt16>] [-Registrar <String>] [-WhatIf [<SwitchParameter>]] [-XmppInternalPort <UInt16>] [-XmppListeningPort <UInt16>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 modifies the internal and external SIP ports for the Edge Server "EdgeServer:atl-edge-001.litwareinc.com".

    Set-CsEdgeServer -Identity "EdgeServer:atl-edge-001.litwareinc.com" -AccessEdgeInternalSipPort 5062 -AccessEdgeExternalSipPort 5062

</div>

<div>

## EXAMPLE 2

Example 2 modifies the internal and external SIP ports for all the Edge Servers located in the Redmond site. To do this, the command first uses the **Get-CsService** cmdlet and the EdgeServer parameter to return a collection of all the Edge Servers currently in use in the organization. That collection is then piped to the **Where-Object** cmdlet, which selects only those Edge servers from the Redmond site; that is, servers where the SiteId property is equal to site:Redmond. This filtered collection is then piped to the **For-Each-Object** cmdlet. That cmdlet runs the **Set-CsEdgeServer** cmdlet against each server in the collection, changing the values assigned to the AccessInternalSipPort and AccessExternalSipPort properties.

    Get-CsService -EdgeServer | Where-Object {$_.SiteId -eq "site:Redmond"} | ForEach-Object {Set-CsEdgeServer -Identity $_.Identity -AccessEdgeInternalSipPort 5062 -AccessEdgeExternalSipPort 5062}

</div>

</div>

<div>

## Detailed Description

Connectivity with the outside world (that is, with the Internet) is an important aspect of Lync Server. Without this connectivity, users would have to log on to the internal network in order to access Lync Server. This would make it difficult for users working off-site to use the software, and preclude the ability of users who do not have accounts in your domain from being able to participate in conferences. Likewise, without connectivity outside of the organization users would be unable to exchange instant messages with federated partners or with people who have accounts on a public instant messaging system such as Yahoo\!, AOL, or MSN.

Edge Servers are used to help provide connectivity between your internal network and the Internet. The **Set-CsEdgeServer** cmdlet enables you to modify configuration settings for your Edge Servers, a task that primarily involves changing the port numbers used for transmitting network traffic.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsEdgeServer** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsEdgeServer"}

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
<td><p><em>AccessEdgeClientSipPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Port used for SIP communications between the Edge Server and client devices. The initial value is set in Topology Builder but can be changed by specifying a new value for this parameter.</p></td>
</tr>
<tr class="even">
<td><p><em>AccessEdgeExternalSipPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Port used for external SIP traffic. The default value is 5061.</p></td>
</tr>
<tr class="odd">
<td><p><em>AccessEdgeInternalSipPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Port used for internal SIP traffic. The default value is 5061.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>DataPsomClientPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Port used for Persistent Shared Object Model (PSOM) communications between the Edge Server and client devices. The initial value is set in Topology Builder but can be changed by specifying a new value for this parameter.</p></td>
</tr>
<tr class="even">
<td><p><em>DataPsomServerPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Port used for PSOM communications between the Edge Server and other servers.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Service location of the Edge Server to be modified. For example: -Identity &quot;EdgeServer:atl-edge-001.litwareinc.com&quot;.</p>
<p>Note that you can leave off the prefix &quot;EdgeServer:&quot; when specifying an Edge server. For example: -Identity &quot;atl-cs-001.litwareinc.com&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><em>MediaCommunicationPortCount</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Total number of ports allocated on the external Edge for media communications. The default value is 10000.</p></td>
</tr>
<tr class="even">
<td><p><em>MediaCommunicationPortStart</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Starting port number on the external Edge for media communications. The default value is 50000.</p></td>
</tr>
<tr class="odd">
<td><p><em>MediaRelayAuthEdgePort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Port used for media relay authentication. The default value is 5062.</p></td>
</tr>
<tr class="even">
<td><p><em>MediaRelayExternalTurnTcpPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Port used for external media relay traffic using the Transmission Control Protocol (TCP). The default value is 444 if your Edge server has a single IP address. If your Edge server has multiple IP addresses then the default value is 443. These values are initially set in Topology Builder but can be changed by specifying a new value for this parameter.</p></td>
</tr>
<tr class="odd">
<td><p><em>MediaRelayExternalTurnUdpPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Port used for external media relay traffic using the User Datagram Protocol (UDP). The default value is 3478.</p></td>
</tr>
<tr class="even">
<td><p><em>MediaRelayInternalTurnTcpPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Port used for internal media relay traffic using TCP. The default value is 443.</p></td>
</tr>
<tr class="odd">
<td><p><em>MediaRelayInternalTurnUdpPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Port used for internal media relay traffic using UDP. The default value is 3478.</p></td>
</tr>
<tr class="even">
<td><p><em>Registrar</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Service location of the Registrar to be associated with the Edge Server. For example: -Registrar &quot;Registrar:atl-cs-001.litwareinc.com&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Describes what would happen if you executed the command without actually executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>XmppInternalPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Port used for internal XMPP traffic. The extensible Messaging and Presence Protocol (XMPP) is an open-standard communications protocol for exchanging messages using XML. An allowed partner is an IM and presence provider whose users are allowed to exchange instant messages and presence information with your Lync Server users. The default value is 5098.</p></td>
</tr>
<tr class="odd">
<td><p><em>XmppListeningPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Listening port for XMPP traffic.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Set-CsEdgeServer** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Set-CsEdgeServer** cmdlet does not return any objects or values. Instead, the cmdlet modifies existing instances of the Microsoft.Rtc.Management.Xds.DisplayEdgeServer object.

</div>

<div>

## See Also


[Get-CsService](get-csservice.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

