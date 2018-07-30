---
title: Test-CsDialPlan
TOCTitle: Test-CsDialPlan
ms:assetid: e6618394-82c5-4bc2-85cc-97ac4686a1aa
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg399024(v=OCS.15)
ms:contentKeyID: 48185687
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Test-CsDialPlan

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-25_

Tests a telephone number against a dial plan (formerly known as a location profile) and returns the normalization rule that will be applied to the number as well as the translated number after the normalization rule has been applied. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Test-CsDialPlan -DialedNumber <PhoneNumber> -Dialplan <LocationProfile>

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example runs a test against the dial plan with the Identity site:Redmond. First the **Get-CsDialPlan** cmdlet is run to retrieve the dial plan with the Identity site:Redmond. That dial plan object is then piped to the **Test-CsDialPlan** cmdlet, where the dial plan is tested against the telephone number 14255559999. The output will be the DialedNumber after a voice normalization rule with a matching pattern has been applied. If there is more than one normalization rule within the site with a matching pattern, the rule with the lowest Priority value will be applied. If there are no rules with patterns matching the DialedNumber value (for example, if the normalization rule matches the pattern for an 11-digit number and you supply a 7-digit number), no value will be returned.

The output of this command includes a phone number and a normalization rule. The normalization rule has numerous properties, and by default this output will be cut off with an ellipsis (...). In order to see all the properties and values of the returned voice normalization rule, we pipe the output to the **Format-List** cmdlet before displaying it to the screen. This will list the phone number and normalization rule on separate lines, and the normalization rule properties and values will wrap to fit on the screen.

    Get-CsDialPlan -Identity site:Redmond | Test-CsDialPlan -DialedNumber 14255559999 | Format-List

</div>

<div>

## EXAMPLE 2

Example 2 is identical to Example 1 except that instead of piping the results of the Get operation directly to the **Test-CsDialPlan** cmdlet, the object is first stored in the variable $a and then is passed as the value to the parameter DialPlan to be used as the dial plan against which the test will run.

As in Example 1, we conclude this command by piping the output to the **Format-List** cmdlet so we can see more information about the voice normalization rule than appears by default.

    $a = Get-CsDialPlan -Identity site:Redmond
    Test-CsDialPlan -DialedNumber 14255559999 -Dialplan $a | Format-List

</div>

<div>

## EXAMPLE 3

This example runs a dial plan test against all dial plans defined within the Lync Server deployment. First the **Get-CsDialPlan** cmdlet is run (with no parameters) to retrieve all the dial plans. The collection of dial plans that is returned is then piped to the **Test-CsDialPlan** cmdlet, where each dial plan in the collection is tested against the telephone number 2065559999. The output will be a list of translated numbers along with the voice normalization rule applied, one for each dial plan in the collection. If no voice normalization rules within a dial plan apply to the DialedNumber value for a particular dial plan (for example, if the normalization rule matches the pattern for an 11-digit number and you supply a 7-digit number) there will be a blank line in the list for that dial plan.

By default, the output cuts off the full display of the voice normalization rule that has been applied. In Examples 1 and 2 we were able to view the entire output by piping the results of the test to the **Format-List** cmdlet. In this example we pipe the output to the **Format-Table** cmdlet and include the Wrap parameter. This shows each entry in table format (one column for the translated number and one for the applied voice normalization rule), but it wraps the output so the normalization rule will wrap within the column.

    Get-CsDialPlan | Test-CsDialPlan -DialedNumber 2065559999 | Format-Table -Wrap

</div>

</div>

<div>

## Detailed Description

This cmdlet allows you to see the results of applying a dial plan to a given telephone number. Dial plans provide information, including how normalization rules are applied, required to enable Enterprise Voice users to make telephone calls. Given a dialed number and a dial plan, this cmdlet will verify which normalization rule within the dial plan will be applied and what the translated number will be.

You can use this cmdlet for troubleshooting issues with number translations or for verifying the application of rules against certain numbers.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Test-CsDialPlan** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsDialPlan"}

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
<td><p><em>DialedNumber</em></p></td>
<td><p>Required</p></td>
<td><p>PhoneNumber</p></td>
<td><p>The phone number against which you want to test the dial plan specified in the Dialplan parameter.</p>
<p>Full Data Type: Microsoft.Rtc.Management.Voice.PhoneNumber</p></td>
</tr>
<tr class="even">
<td><p><em>Dialplan</em></p></td>
<td><p>Required</p></td>
<td><p>LocationProfile</p></td>
<td><p>An object containing a reference to the dial plan against which you want to test the number specified in the DialedNumber parameter.</p>
<p>Full Data Type: Microsoft.Rtc.Management.WritableConfig.Policy.Voice.LocationProfile</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.LocationProfile object. Accepts pipelined input of dial plan objects.

</div>

<div>

## Return Types

Returns an object of type Microsoft.Rtc.Management.Voice.LocationProfileTestResult.

</div>

<div>

## See Also


[New-CsDialPlan](new-csdialplan.md)  
[Remove-CsDialPlan](remove-csdialplan.md)  
[Set-CsDialPlan](set-csdialplan.md)  
[Get-CsDialPlan](get-csdialplan.md)  
[Grant-CsDialPlan](grant-csdialplan.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

