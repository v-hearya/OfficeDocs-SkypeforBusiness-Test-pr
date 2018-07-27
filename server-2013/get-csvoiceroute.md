---
title: Get-CsVoiceRoute
TOCTitle: Get-CsVoiceRoute
ms:assetid: 422abb2d-bff3-4b9a-b18c-d8202b01f69b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425926(v=OCS.15)
ms:contentKeyID: 48183967
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsVoiceRoute

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Returns information about the voice routes configured for use in an organization. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsVoiceRoute [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsVoiceRoute [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Retrieves the properties for all voice routes defined within the organization.

    Get-CsVoiceRoute

</div>

<div>

## EXAMPLE 2

Retrieves the properties for the Route1 voice route.

    Get-CsVoiceRoute -Identity Route1

</div>

<div>

## EXAMPLE 3

This command displays voice route settings where the Identity contains the string "test" anywhere within the value. To find the string test only at the end of the Identity, use the value \*test. Similarly, to find the string test only if it occurs at the beginning of the Identity, specify the value test\*.

    Get-CsVoiceRoute -Filter *test*

</div>

<div>

## EXAMPLE 4

This command retrieves all voice routes that have not had any PSTN gateways assigned. First all voice routes are retrieved using the **Get-CsVoiceRoute** cmdlet. These voice routes are then piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet narrows down the results of the Get operation. In this case we look at each voice route (that’s what the $\_ represents) and check the Count property of the PstnGatewayList property. If the count of PSTN gateways is 0, the list is empty and no gateways have been defined for the route.

    Get-CsVoiceRoute | Where-Object {$_.PstnGatewayList.Count -eq 0}

</div>

</div>

<div>

## Detailed Description

Use this cmdlet to retrieve one or more existing voice routes. Voices routes contain instructions that tell Lync Server how to route calls from Enterprise Voice users to phone numbers on the public switched telephone network (PSTN) or a private branch exchange (PBX).

This cmdlet can be used to retrieve voice route information such as which PSTN gateways the route is associated with (if any), which PSTN usages are associated with the route, the pattern (in the form of a regular expression) that identifies the phone numbers to which the route applies, and caller ID settings. The PSTN usage associates the voice route to a voice policy.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsVoiceRoute** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsVoiceRoute"}

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
<td><p>This parameter filters the results of the Get operation based on the wildcard value passed to this parameter.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>A string that uniquely identifies the voice route. If no identity is provided, all voice routes for the organization are returned.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the voice route from the local replica of the Central Management store, rather than the Central Management store itself.</p></td>
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

This cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route object.

</div>

<div>

## See Also


[New-CsVoiceRoute](new-csvoiceroute.md)  
[Remove-CsVoiceRoute](remove-csvoiceroute.md)  
[Set-CsVoiceRoute](set-csvoiceroute.md)  
[Test-CsVoiceRoute](test-csvoiceroute.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

