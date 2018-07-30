---
title: New-CsNetworkBWAlternatePath
TOCTitle: New-CsNetworkBWAlternatePath
ms:assetid: 9017378e-4583-42bc-9572-aa8e9571cfe3
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398732(v=OCS.15)
ms:contentKeyID: 48184830
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsNetworkBWAlternatePath

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-25_

Creates new settings that define whether media can be routed to alternate paths through the Internet for bandwidth-constrained connections. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    New-CsNetworkBWAlternatePath -AlternatePath <$true | $false> -BWPolicyModality <Audio | Video>

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example creates a new network bandwidth alternate path and assigns those settings to a newly created region. The first line in the example calls the **New-CsNetworkBWAlternatePath** cmdlet to create a new alternate path. An alternate path has only two properties: BWPolicyModality, which must be set to either audio or video (in this example, audio is used); and AlternatePath, which must be either True or False (in this example, True is used). We assign the output from this cmdlet, which is a reference to the alternate path object just created, to the variable $a.

In line 2 of this example we use this newly created alternate path in the creation of a new network region. To do this we call the **New-CsNetworkRegion** cmdlet, passing an Identity of NorthAmerica. We assign a value for the required parameter CentralSite (in this example the name of the central site for this region is Redmond-NA-MLS), and then we specify the BWAlternatePaths parameter, passing it the variable ($a) containing the alternate path object we just create.

    $a = New-CsNetworkBWAlternatePath -BWPolicyModality "audio" -AlternatePath $true
    New-CsNetworkRegion -Identity NorthAmerica -CentralSite Redmond-NA-MLS -BWAlternatePaths $a

</div>

</div>

<div>

## Detailed Description

Within a call admission control (CAC) configuration in Lync Server, there are two possible modalities: audio and video. Bandwidth limitations can be set on each of these modalities. When bandwidth limitations will prevent a call from completing, it may be possible for the call to take an alternate path through the Internet that will enable the call to be established. This cmdlet allows you to create the settings that define whether a call can be routed to an alternate path through the Internet based on modality. The settings apply per region within the CAC configuration.

This cmdlet does not immediately save the newly created settings. Instead, it creates the settings in memory. To apply these settings to a region within the network, you need to assign the output of the cmdlet to a variable, and then use that variable as a value to the BWAlternatePaths parameter of the **New-CsNetworkRegion** cmdlet or the **Set-CsNetworkRegion** cmdlet. Note that you can apply these settings directly by using the AudioAlternatePath and VideoAlternatePath parameters of the **New-CsNetworkRegion** cmdlet and the **Set-CsNetworkRegion** cmdlet, without having to call the **New-CsNetworkBWAlternatePath** cmdlet to create a new object.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsNetworkBWAlternatePath** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsNetworkBWAlternatePath"}

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
<td><p><em>AlternatePath</em></p></td>
<td><p>Required</p></td>
<td><p>Boolean</p></td>
<td><p>Set the parameter to True to allow calls made in the media of the modality specified in the BWPolicyModality parameter (either audio or video) to be routed through an alternate path if adequate bandwidth does not exist in the primary path.</p></td>
</tr>
<tr class="even">
<td><p><em>BWPolicyModality</em></p></td>
<td><p>Required</p></td>
<td><p>BWPolicyModality</p></td>
<td><p>The modality to which the alternate path setting applies.</p>
<p>Valid values: audio, video</p>
<p>Full data type: Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyModality</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None.

</div>

<div>

## Return Types

Creates an object of type Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWAlternatePathType.

</div>

<div>

## See Also


[New-CsNetworkRegion](new-csnetworkregion.md)  
[Set-CsNetworkRegion](set-csnetworkregion.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

