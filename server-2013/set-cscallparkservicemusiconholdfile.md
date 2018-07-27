---
title: Set-CsCallParkServiceMusicOnHoldFile
TOCTitle: Set-CsCallParkServiceMusicOnHoldFile
ms:assetid: af5e7573-4bfd-47b1-a92b-83b06a537158
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412836(v=OCS.15)
ms:contentKeyID: 48185140
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsCallParkServiceMusicOnHoldFile

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-07_

Changes the audio file that will be played to callers who are on hold in a parked call. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsCallParkServiceMusicOnHoldFile -Content <Byte[]> -Service <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example sets the file SoothingMusic.wma to be the audio file that is played to callers whose calls are parked. The first line of this example is a call to the **Get-Content** cmdlet. This cmdlet simply reads the contents of a file and assigns them, in this case, to the variable $a. We pass a value of 0 to the ReadCount parameter so the **Get-Content** cmdlet will read the entire file at once (rather than try to read it line by line, which doesn’t apply to an audio file). We set the Encoding parameter to byte. This tells the **Get-Content** cmdlet that the content we want to read into variable $a is a byte array rather than the audio file in .wma format.

Line 2 in this example is where we actually assign the audio file. We call the **Set-CsCallParkServiceMusicOnHoldFile** cmdlet and specify the service ID where the Call Park service is running. We then pass the audio file contents that we read into variable $a to the Content parameter. (Remember that these contents must be in byte format.)

    $a = Get-Content -ReadCount 0 -Encoding byte "C:\MoHFiles\soothingmusic.wma"
    Set-CsCallParkServiceMusicOnHoldFile -Service ApplicationServer:pool0.litwareinc.com -Content $a

</div>

</div>

<div>

## Detailed Description

Call parking is a service that allows a user to "park" an incoming phone call. Parking a call transfers it to a number in a specified range and immediately places it on hold. Based on configuration settings for the Call Park service, music on hold can be played to the caller while the call is parked. Use this cmdlet to change the audio file (music on hold) that is played to a parked caller who is on hold.

Music on hold is played only if the EnableMusicOnHold property of the Call Park service has been set to True. You can check this property by calling the **Get-CsCpsConfiguration** cmdlet. You can set the property either when the Call Park configuration is created with the **New-CsCpsConfiguration** cmdlet or after the Call Park configuration exists by calling the **Set-CsCpsConfiguration** cmdlet. This property is True by default.

Lync Server ships with a default Call Park service music on hold file. If you don’t assign an audio file, the default file will be used.

Audio files must be in the following format: Windows Media Audio 9, 44 kHz, 16 bits, Mono, CBR, or 32 kbps.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsCallParkServiceMusicOnHoldFile** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsCallParkServiceMusicOnHoldFile"}

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
<td><p><em>Content</em></p></td>
<td><p>Required</p></td>
<td><p>System.Byte[]</p></td>
<td><p>The contents of the audio file in byte format.</p>
<p>Use the <strong>Get-Content</strong> cmdlet to retrieve the contents of the audio file in byte format. (For details, see the Examples section in this topic.)</p></td>
</tr>
<tr class="even">
<td><p><em>Service</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>The ID of the service where the Call Park service resides; for example, ApplicationServer:pool0.litwareinc.com.</p></td>
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
<td><p>Suppresses any confirmation prompts that would otherwise be displayed before making changes.</p></td>
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

Byte\[\]. Accepts pipelined input of a byte array containing the music on hold file.

</div>

<div>

## Return Types

This cmdlet does not return a value.

</div>

<div>

## See Also


[New-CsCpsConfiguration](new-cscpsconfiguration.md)  
[Remove-CsCpsConfiguration](remove-cscpsconfiguration.md)  
[Set-CsCpsConfiguration](set-cscpsconfiguration.md)  
[Get-CsCpsConfiguration](get-cscpsconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

