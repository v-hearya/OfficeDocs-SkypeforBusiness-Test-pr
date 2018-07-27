---
title: Set-CsConferenceServer
TOCTitle: Set-CsConferenceServer
ms:assetid: 90f9f1f1-0029-4f97-a8f4-719523cfad56
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398738(v=OCS.15)
ms:contentKeyID: 48184840
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsConferenceServer

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-07_

Modifies the properties of an A/V Conferencing Server (also known as a Conference Server). The Conference Server provides audio and video (A/V) capabilities to your conferences. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsConferenceServer [-Identity <XdsGlobalRelativeIdentity>] [-AppSharingPortCount <UInt16>] [-AppSharingPortStart <UInt16>] [-AppSharingSipPort <UInt16>] [-AudioPortCount <UInt16>] [-AudioPortStart <UInt16>] [-AudioVideoSipPort <UInt16>] [-Confirm [<SwitchParameter>]] [-DataPsomPort <UInt16>] [-EdgeServer <String>] [-Force <SwitchParameter>] [-ImSipPort <UInt16>] [-MeetingPsomPort <UInt16>] [-PhoneSipPort <UInt16>] [-VideoPortCount <UInt16>] [-VideoPortStart <UInt16>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 modifies the instant messaging SIP port for the Conference Server ConferencingServer:atl-cs-001.litwareinc.com. In this example, the port is changed to 5075.

    Set-CsConferenceServer -Identity "ConferencingServer:atl-cs-001.litwareinc.com" -ImSipPort 5075

</div>

<div>

## EXAMPLE 2

Example 2 is a variation of the command shown in Example 1; in this case, however, the instant messaging SIP port is changed for all the Conference Servers in the organization. To do this, the command first uses the **Get-CsService** cmdlet and the ConferencingServer parameter to return a collection of all the Conferencing Servers currently in use. That collection is then piped to the **ForEach-Object** cmdlet, which runs the **Set-CsConferenceServer** cmdlet against each server in the collection, setting the ImSipPort to 5075.

    Get-CsService -ConferencingServer | ForEach-Object {Set-CsConferenceServer -Identity $_.Identity -ImSipPort 5075}

</div>

</div>

<div>

## Detailed Description

Conference Servers (also known as A/V Conferencing Servers) are used to provide audio and video capabilities to conferences. In turn, the **Set-CsConferenceServer** cmdlet can be used to modify the properties of these servers; in particular, you can specify which ports are used for such things as audio traffic, video traffic, and application sharing. You can also use the **Set-CsConferenceServer** cmdlet to associate a given server with a Edge Server or Archiving Server.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsConferenceServer** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsConferenceServer"}

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
<td><p><em>AppSharingPortCount</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Total number of ports allocated for application sharing. The actual ports to be opened will start with the value configured for AppSharingPortStart and continue through the number of ports specified for AppSharingPortCount. For example, if the AppSharingPortStart is set to 60000 and the AppSharingPortCount is set to 100, then ports 60000 through 60099 will be used for application sharing.</p></td>
</tr>
<tr class="even">
<td><p><em>AppSharingPortStart</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>First port in the range of media ports allocated for application sharing. For example: –AppSharingPortStart 60000.</p></td>
</tr>
<tr class="odd">
<td><p><em>AppSharingSipPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>SIP port used to listen for requests for application sharing. The ports actually used for application sharing are configured using AppSharingPortStart and AppSharingPortCount.</p></td>
</tr>
<tr class="even">
<td><p><em>AudioPortCount</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Total number of ports allocated for sending and receiving audio traffic. The actual ports to be opened will start with the value configured for AudioPortStart and continue through the number of ports specified for AudioPortCount. For example, if the AudioPortStart is set to 60000 and the AudioPortCount is set to 100, then ports 60000 through 60099 will be used for audio traffic.</p></td>
</tr>
<tr class="odd">
<td><p><em>AudioPortStart</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>First port in the range of media ports allocated for sending and receiving audio traffic. For example: –AudioPortStart 60000.</p></td>
</tr>
<tr class="even">
<td><p><em>AudioVideoSipPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>SIP port used to listen for incoming requests for audio and video service. The ports actually used for audio and video traffic are configured using AudioPortCount, AudioPortStart, VideoPortCount, and VideoPortStart.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>DataPsomPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Data port used by the Persistent Shared Object Model (PSOM) protocol.</p></td>
</tr>
<tr class="odd">
<td><p><em>EdgeServer</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Service location of the Edge Server to be associated with the Conference Server. For example: -EdgeServer &quot;EdgeServer:atl-edge-001.litwareinc.com&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Service location of the Conference Server to be modified. For example: -Identity &quot;ConferencingServer:atl-cs-001.litwareinc.com&quot;.</p>
<p>Note that you can leave off the prefix &quot;ConferencingServer:&quot; when specifying a Conference Server. For example: -Identity &quot;atl-cs-001.litwareinc.com&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>ImSipPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Port used for instant messaging traffic.</p></td>
</tr>
<tr class="odd">
<td><p><em>MeetingPsomPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Port used for the Persistent Shared Object Model (PSOM) protocol, a Microsoft protocol used for conferences.</p></td>
</tr>
<tr class="even">
<td><p><em>PhoneSipPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Port used for telephony traffic.</p></td>
</tr>
<tr class="odd">
<td><p><em>VideoPortCount</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>Total number of ports allocated for sending and receiving video traffic. The actual ports to be opened will start with the value configured for VideoPortStart and continue through the number of ports specified for VideoPortCount. For example, if the VideoPortStart is set to 60000 and the VideoPortCount is set to 100, then ports 60000 through 60099 will be used for video traffic.</p></td>
</tr>
<tr class="even">
<td><p><em>VideoPortStart</em></p></td>
<td><p>Optional</p></td>
<td><p>System.UInt16</p></td>
<td><p>First port in the range of ports allocated for sending and receiving video traffic. For example: –VideoPortStart 60000.</p></td>
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

<div>

## Input Types

None. The **Set-CsConferenceServer** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Set-CsConferenceServer** cmdlet does not return any objects or values. Instead, the cmdlet modifies existing instances of the Microsoft.Rtc.Management.Xds.DisplayConferenceServer object.

</div>

<div>

## See Also


[Get-CsConferencingConfiguration](get-csconferencingconfiguration.md)  
[Get-CsService](get-csservice.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

