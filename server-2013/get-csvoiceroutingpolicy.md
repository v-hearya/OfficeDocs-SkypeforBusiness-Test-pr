---
title: Get-CsVoiceRoutingPolicy
TOCTitle: Get-CsVoiceRoutingPolicy
ms:assetid: 60245b7d-4e95-4925-aae5-c0fa1e9f38fc
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204940(v=OCS.15)
ms:contentKeyID: 48184271
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsVoiceRoutingPolicy

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Returns information about the voice routing policies configured for use in your organization. Voice routing policies manage PSTN usages for users of hybrid voice. Hybrid voice enables users homed on Lync Online to take advantage of the Enterprise Voice capabilities available in an on-premises installation of Lync Server 2013. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Get-CsVoiceRoutingPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsVoiceRoutingPolicy [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 returns information for all the voice routing policies configured for use in the organization.

    Get-CsVoiceRoutingPolicy

</div>

<div>

## Example 2

In Example 2, information is returned for a single voice routing policy: the policy with the Identity RedmondVoiceRoutingPolicy.

    Get-CsVoiceRoutingPolicy -Identity "RedmondVoiceRoutingPolicy"

</div>

<div>

## Example 3

The command shown in Example 3 returns information about all the voice routing policies configured at the per-user scope. To do this, the command uses the Filter parameter and the filter value "tag:\*"; that filter value limits the returned data to policies that have an Identity that begins with the string value "tag:".

    Get-CsVoiceRoutingPolicy -Filter "tag:*"

</div>

<div>

## Example 4

In Example 4, information is returned only for those voice routing policies that include the PSTN usage "Long Distance". To carry out this task, the command first calls the **Get-CsVoiceRoutingPolicy** cmdlet without any parameters; that returns a collection of all the voice routing policies configured for use in the organization. This collection is then piped to the **Where-Object** cmdlet, which picks out only those policies where the PstnUsages property includes (-contains) the usage "Long Distance".

    Get-CsVoiceRoutingPolicy | Where-Object {$_.PstnUsages -contains "Long Distance"}

</div>

<div>

## Example 5

Example 5 is a variation on the command shown in Example 4; in this case, however, information is returned only for those voice routing policies that do not include the PSTN usage "Long Distance". In order to do that, the **Where-Object** cmdlet uses the –notcontains operator, which limits returned data to policies that do not include the usage "Long Distance".

    Get-CsVoiceRoutingPolicy | Where-Object {$_.PstnUsages -notcontains "Long Distance"}

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

Voice routing policies are used in "hybrid" scenarios: when some of your users are homed on the on-premises version of Lync Server and other users are homed on Lync Online. Assigning your Lync Online users a voice routing policy enables those users to receive and to place phones calls to the public switched telephone network by using your on-premises SIP trunks.

Note that simply assigning a user a voice routing policy will not enable them to make PSTN calls via Lync Online. Among other things, you will also need to enable those users for Enterprise Voice and will need to assign them an appropriate voice policy and dial plan.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsVoiceRoutingPolicy"}

**Lync Server Control Panel:** The functions carried out by the Get-CsVoiceRoutingPolicy cmdlet are not available in the Lync Server Control Panel.

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
<td><p>Enables you to use wildcards when retrieving one or more voice routing policies. For example, to return all the policies configured at the per-user scope, use this syntax:</p>
<p>-Filter &quot;tag:*&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Unique identifier of the voice routing policy to be retrieved. To return the global policy, use this syntax:</p>
<p>-Identity global</p>
<p>To return a policy configured at the per-user scope, use syntax like this:</p>
<p>-Identity &quot;RedmondVoiceRoutingPolicy&quot;</p>
<p>You cannot use wildcard characters when specifying the Identity.</p>
<p>If neither the Identity nor the Filter parameters are specified, then the <strong>Get-CsVoiceRoutingPolicy</strong> cmdlet returns all the voice routing policies configured for use in the organization.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the voice policy data from the local replica of the Central Management store rather than from the Central Management store itself.</p></td>
</tr>
</tbody>
</table>


</div>

<span id="InputTypes"></span>

<div>

## Input Types

None. The **Get-CsVoiceRoutingPolicy** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **Get-CsVoiceRoutingPolicy** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoiceRoutingPolicy object.

</div>

<div>

## See Also


[Grant-CsVoiceRoutingPolicy](grant-csvoiceroutingpolicy.md)  
[New-CsVoiceRoutingPolicy](new-csvoiceroutingpolicy.md)  
[Remove-CsVoiceRoutingPolicy](remove-csvoiceroutingpolicy.md)  
[Set-CsVoiceRoutingPolicy](set-csvoiceroutingpolicy.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

