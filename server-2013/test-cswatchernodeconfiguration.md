---
title: Test-CsWatcherNodeConfiguration
TOCTitle: Test-CsWatcherNodeConfiguration
ms:assetid: 085507a1-17e8-4dfa-aa6a-062620584335
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204652(v=OCS.15)
ms:contentKeyID: 48183333
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Test-CsWatcherNodeConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Verifies the watcher node configuration settings in use in your organization. Watcher nodes are computers that periodically use Microsoft System Center Operations Manager and Lync Server 2013 synthetic transactions to verify that Lync Server components are working as expected. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Test-CsWatcherNodeConfiguration [-FileName <String>] [-ReadCredentialsFromCurrentUserStore <SwitchParameter>]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 verifies the configuration settings for each watcher node in use in the organization.

    Test-CsWatcherNodeConfiguration

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

If you are using Microsoft System Center Operations Manager to monitor Lync Server 2013 then you have the option of setting up "watcher nodes": computers that periodically, and automatically, run synthetic transactions in order to verify that Lync Server is working as expected. Watcher nodes are assigned to pools, and are managed using the **CsWatcherNodeConfiguration** cmdlets. Note that you do not need to install watcher nodes if you are using System Center Operations Manager. You can still monitor your system without using watcher nodes; the only difference is that any synthetic transactions you want to run will need to be invoked manually rather than automatically invoked by Operations Manager.

The **Test-CsWatcherNodeConfiguration** cmdlet provides a way for you to verify that a watcher node has been correctly configured and is assigned to a valid Lync Server 2013 pool. Note that the **Test-CsWatcherNodeConfiguration** cmdlet must be run on the watcher node itself; the cmdlet cannot be run against remote computers.

**Lync Server Control Panel:** The functions carried out by the **Test-CsWatcherNodeConfiguration** cmdlet are not available in the Lync Server Control Panel.

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
<td><p><em>FileName</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to specify a file path for the log file created when the cmdlet runs. For example:</p>
<p>-Report &quot;C:\Logs\WatcherNode.html&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>ReadCredentialsFromCurrentUserStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>When present, instructs the <strong>Test-CsWatcherNodeConfiguration</strong> cmdlet to retrieve the user credentials from the user's credentials store. By default, the <strong>Test-CsWatcherNodeConfiguration</strong> cmdlet looks for credentials in the network service account's credentials store.</p></td>
</tr>
</tbody>
</table>


</div>

<span id="InputTypes"></span>

<div>

## Input Types

None. The **Test-CsWatcherNodeConfiguration** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **Test-CsWatcherNodeConfiguration** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.

</div>

<div>

## See Also


[Get-CsWatcherNodeConfiguration](get-cswatchernodeconfiguration.md)  
[New-CsWatcherNodeConfiguration](new-cswatchernodeconfiguration.md)  
[Remove-CsWatcherNodeConfiguration](remove-cswatchernodeconfiguration.md)  
[Set-CsWatcherNodeConfiguration](set-cswatchernodeconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

