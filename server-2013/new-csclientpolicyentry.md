---
title: New-CsClientPolicyEntry
TOCTitle: New-CsClientPolicyEntry
ms:assetid: e975d048-4911-4ae6-9446-2a6363726a4a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg399046(v=OCS.15)
ms:contentKeyID: 48185898
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsClientPolicyEntry

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Adds new options to Lync Server client policies. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    New-CsClientPolicyEntry -Name <String> -Value <String>

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The commands shown in Example 1 demonstrate how a new policy entry can be added to the global client policy. This example adds a new feedback option to Lync. Note that this example is for demonstration purposes. You should not expect to be able to run these commands and add a similar feedback option to your copy of Lync.

In order to add the new policy entry, the first command in the example uses the **New-CsClientPolicyEntry** cmdlet to create an entry with the Name OnlineFeedbackURL and the Value http://www.litwareinc.com/feedback. The resulting policy entry object is stored in a variable named $x.

In the second command, the **Get-CsClientPolicy** cmdlet is used to create an object reference ($y) to the global client policy. After the object reference has been created, the Add method is used to add the new policy entry to the PolicyEntry property. If PolicyEntry already has one or more entries, the new value will simply be appended to the end of that collection.

Finally, the last command in the example uses the **Set-CsClientPolicy** cmdlet to write the changes to the actual global policy. If you do not call the **Set-CsClientPolicy** cmdlet, your changes will exist only in memory, and will disappear as soon as you end your Windows PowerShell session or delete the variable $x.

    $x = New-CsClientPolicyEntry -Name "OnlineFeedbackURL" -Value "http://www.litwareinc.com/feedback"
    
    $y = Get-CsClientPolicy -Identity global
    $y.PolicyEntry.Add($x)
    
    Set-CsClientPolicy -Instance $y

</div>

<div>

## EXAMPLE 2

Example 2 is a variation of the commands shown in Example 1. In this case, however, the new policy entry replaces all the items currently in the global policy’s PolicyEntry property. To do that, the first command in the example creates a new policy entry that is stored in a variable named $x. The second command then uses the **Set-CsClientPolicy** cmdlet to set the value of the PolicyEntry property to $x. After the command finishes running the only item in the PolicyEntry property will be the new entry. Any items contained in that property before the **Set-CsClientPolicy** cmdlet was called will have replaced by the new entry.

    $x = New-CsClientPolicyEntry -Name "OnlineFeedbackURL" -Value "http://www.litwareinc.com/feedback"
    Set-CsClientPolicy -Identity global -PolicyEntry $x

</div>

<div>

## EXAMPLE 3

Example 3 demonstrates how you can remove a client policy entry from the global policy. To do this, the first command in the example retrieves the global client policy and stores that information in a variable named $y.

After the global policy has been retrieved, the second command in the example uses the RemoveAt() method to delete the first policy entry in that policy. The policy entry to be removed is indicated by its index number: the first policy entry has an index number of 0, the second policy entry has an index number of 1, and so on. The syntax RemoveAt(0) means that the first policy entry will be removed.

As soon as the policy entry has been removed from the in-memory instance of the global policy, the **Set-CsClientPolicy** cmdlet is then called in order to write these changes to the actual instance of the global client policy.

    $y = Get-CsClientPolicy -Identity global
    $y.PolicyEntry.RemoveAt(0)
    
    Set-CsClientPolicy -Instance $y 

</div>

<div>

## EXAMPLE 4

The command shown in Example 4 removes all the client policy entries configured for the global policy. This is done by using the PolicyEntry parameter and setting the parameter value to null ($Null).

    Set-CsClientPolicy -Identity global -PolicyEntry $Null

</div>

</div>

<div>

## Detailed Description

Client policies are the primary mechanism used by Lync Server to manage client software such as Lync. When you create or configure a client policy, you have numerous options available to you; for example, you can specify whether or not photos should be used in Lync, whether or not emoticons are allowed in instant messages, and whether or not Lync automatically saves transcripts of instant messaging sessions. These options cover many of the client-related settings that administrators need to manage.

However, they might not cover all the client settings that administrators need to manage. In order to add management flexibility and extensibility, client policies include a property named PolicyEntry. This multi-valued property enables administrators to add new management options that are not explicitly called out in client policies. For example, prior to the release of Lync Server, beta testers were given the ability to add a feedback option to Lync. This option was added as a new policy entry, and was created using the **New-CsClientPolicyEntry** cmdlet.

Note that you cannot arbitrarily create new policy entries and expect those entries to manage Lync or some other client applications. Instead, you will need to wait for notification from Microsoft regarding names and values that can be used to construct new client policy entries.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsClientPolicyEntry** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsClientPolicyEntry"}

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
<td><p><em>Name</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Name of the new policy entry. For example: -Name &quot;OnlineFeedbackURL&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Value</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Value to be assigned to the new policy entry. For example: -Value http://www.litwareinc.com/feedback.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The New-CsClientPolicyEntry cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **New-CsClientPolicyEntry** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Client.PolicyEntryType object.

</div>

<div>

## See Also


[New-CsClientPolicy](new-csclientpolicy.md)  
[Set-CsClientPolicy](set-csclientpolicy.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

