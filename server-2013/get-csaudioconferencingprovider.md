---
title: Get-CsAudioConferencingProvider
TOCTitle: Get-CsAudioConferencingProvider
ms:assetid: 4632e9d0-aa87-459f-ad7e-27125c11da5b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ994030(v=OCS.15)
ms:contentKeyID: 51803939
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsAudioConferencingProvider

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Returns information about the audio conferencing providers authorized for use in the organization. Audio conferencing providers are a third-party companies that provide organizations with conferencing services.

The **Get-CsAudioConferencingProvider** cmdlet can only be used with Microsoft Lync Online.

<div>

## Syntax

    Get-CsAudioConferencingProvider [[-Identity] <XdsGlobalRelativeIdentity>] [-LocalStore][<CommonParameters>]Get-CsAudioConferencingProvider [-Filter <string>] [-LocalStore] [<CommonParameters>]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 returns information about all the audio conferencing providers available for use in your organization.

    Get-CsAudioConferencingProvider

</div>

<div>

## Example 2

In Example 2, information is returned for a single audio conferencing provider: the provider with the Identity Fabrikam Telecom.

    Get-CsAudioConferencingProvider -Identity "Fabrikam Telecom"

</div>

<div>

## Example 3

Example 3 demonstrates how wildcard values (and the Filter parameter) can be used to return information about audio conferencing providers. In this example, the filter value "\*Fabrikam\*" returns all audio conferencing providers that have the string value "Fabrikam" anywhere in their Identity.

    Get-CsAudioConferencingProvider -Filter "*Fabrikam*"

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

An audio conferencing provider is a third-party company that provides organizations with conferencing services. Among other things, audio conferencing providers provide a way for users located off site, and not connected to the corporate network or the Internet, to participate in the audio portion of a conference or meeting. Audio conferencing providers often provide high-end services such as live translation, transcription, and live per-conference operator assistance.

After organizations have contracted with an audio conferencing provider, users can be assigned to the provider by using the **Set-CsUserAcp** cmdlet. Administrators can retrieve information about the audio conferencing providers available to them by using the **Get-CsAudioConferencingProvider** cmdlet.

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
<td><p>Enables you to use wildcard characters when indicating the audio conferencing provider (or providers) to be returned. For example, this syntax returns information about all the audio conferencing providers that have the string value &quot;fabrikam&quot; somewhere in their Identity:</p>
<p>-Filter &quot;*fabrikam*&quot;</p>
<p>Note that you cannot use the Filter parameter and the Identity parameters in the same command.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Unique identifier for the audio conferencing provider to be returned. For example:</p>
<p>-Identity &quot;Fabrikam Telecom&quot;</p>
<p>If neither the Identity parameter nor the Filter parameter are included in a command then the <strong>Get-CsAudioConferencingProvider</strong> cmdlet returns information for all the available providers.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the audio conferencing provider data from the local replica of the Central Management store rather than from the Central Management store itself.</p></td>
</tr>
</tbody>
</table>


</div>

<span id="InputTypes"></span>

<div>

## Input Types

None. The **Get-CsAudioConferencingProvider** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **Get-CsAudioConferencingProvider** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.AudioConferencingProvider.AudioConferencingProvider\#Decorated object.

</div>

<div>

## See Also


[Get-CsUserAcp](get-csuseracp.md)  
[Remove-CsUserAcp](remove-csuseracp.md)  
[Set-CsUserAcp](set-csuseracp.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

