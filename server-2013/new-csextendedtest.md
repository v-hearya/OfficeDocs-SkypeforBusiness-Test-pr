---
title: New-CsExtendedTest
TOCTitle: New-CsExtendedTest
ms:assetid: d4756daa-a4ce-4d74-926b-89754cf7e0b2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205275(v=OCS.15)
ms:contentKeyID: 48185459
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsExtendedTest

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Creates a PSTN or an Audio Conferencing Provider test that can then be assigned to a watcher node configuration. Watcher nodes are computers that periodically use Microsoft System Center Operations Manager and Lync Server 2013 synthetic transactions to verify that Lync Server components are working as expected. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    New-CsExtendedTest -Name <String> -TestType <AudioConferencingProvider | PSTN> [-TestUsers <PSListModifier>]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The commands shown in Example 1 create a new extended test (with the TestType of PSTN), then adds that extended test to a new watcher node for the pool atl-cs-001.litwareinc.com. In the first command in the example, the **New-CsExtendedTest** cmdlet is used to create an extended test named PSTN Test; this test includes the test users sip:kenmyer@litwareinc.com and sip:pilar@litwareinc.com. (Note that these two test users must have already been configured using the **Set-CsTestUserCredential** cmdlet.) The resulting extended test object is then stored in a variable named $x.

In the second command, the new extended test is added to the newly-created watcher node for atl-cs-001.litwareinc.com. This is done by using the ExtendedTests parameter and the syntax @{Add=$x}.

    $x = New-CsExtendedTest -TestUsers "sip:kenmyer@litwareinc.com", "sip:pilar@litwareinc.com" -Name "PSTN Test" -TestType "PSTN"
    
    New-CsWatcherNodeConfiguration -TargetFqdn "atl-cs-001.litwareinc.com" -PortNumber 5061 -TestUsers "sip:kenmyer@litwareinc.com","sip:pilar@litwareinc.com" -ExtendedTests @{Add=$x}

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

If you are using Microsoft System Center Operations Manager to monitor Lync Server 2013 then you have the option of setting up "watcher nodes": computers that periodically, and automatically, run synthetic transactions in order to verify that Lync Server is working as expected. Watcher nodes are assigned to pools, and are managed using the CsWatcherNodeConfiguration cmdlets. Note that you do not need to install watcher nodes if you are using System Center Operations Manager. You can still monitor your system without using watcher nodes; the only difference is that any synthetic transactions you want to run will need to be invoked manually rather than automatically invoked by Operations Manager.

When you configure a watcher node, you have the option of adding a PSTN or an Audio Conferencing Provider test as an "extended test"; these extended tests can be used instead of or in addition to the standard set of tests run by a watcher node computer. Extended tests must be created using the **New-CsExtendedTest** cmdlet and then added to the appropriate watcher node.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsExtendedTest"}

**Lync Server Control Panel:** The functions carried out by the **New-CsExtendedTest** cmdlet are not available in the Lync Server Control Panel.

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
<td><p>Friendly name to be given to the extended test.</p></td>
</tr>
<tr class="even">
<td><p><em>TestType</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.WatcherNode.TestType</p></td>
<td><p>Type of testing to be carried out by the extended test. Allowed values are:</p>
<p>* PSTN</p>
<p>* AudioConferencingProvider</p>
<p>You can only specify a single TestType per extended test.</p></td>
</tr>
<tr class="odd">
<td><p><em>TestUsers</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>SIP address of the user account(s) that will serve as test users. Multiple accounts can be specified by separating those accounts using commas; for example:</p>
<p>–TestUsers &quot;sip:kenmyer@litwareinc.com&quot;, &quot;sip:pilar@litwareinc.com&quot;</p>
<p>You must specify at least two test users when using the PSTN TestType.</p></td>
</tr>
</tbody>
</table>


</div>

<span id="InputTypes"></span>

<div>

## Input Types

None. The **New-CsExtendedTest** cmdlet does not accept pipelined input

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **New-CsExtendedTest** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.WatcherNode.ExtendedTest object.

</div>

<div>

## See Also


[New-CsWatcherNodeConfiguration](new-cswatchernodeconfiguration.md)  
[Set-CsWatcherNodeConfiguration](set-cswatchernodeconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

