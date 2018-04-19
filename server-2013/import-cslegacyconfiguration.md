---
title: Import-CsLegacyConfiguration
TOCTitle: Import-CsLegacyConfiguration
ms:assetid: bd688c08-abb8-4c78-8e1b-b330412d4422
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412923(v=OCS.15)
ms:contentKeyID: 48185268
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Import-CsLegacyConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

The **Import-CsLegacyConfiguration** cmdlet enables you to import a number of configuration settings from Microsoft Office Communications Server 2007 R2 or Microsoft Office Communications Server 2007 to Lync Server. This helps provide interoperability between Lync Server and your earlier installation of Office Communications Server 2007 R2 or Office Communications Server 2007. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Import-CsLegacyConfiguration [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-ReplaceExisting <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 merges voice policies and other settings from Communications Server 2007 or Communications Server 2007 R2 with an installation of Lync Server.

    Import-CsLegacyConfiguration

</div>

<div>

## EXAMPLE 2

The command shown in Example 2 is a variation of the command shown in Example 1. In this case, however, the ReplaceExisting parameter is included. This parameter instructs the cmdlet to use the imported data to resolve name collisions. For example, suppose you try to import a voice route named LocalRoute, and a voice route by that name already exists in your Lync Server installation. Because you included the ReplaceExisting parameter, the Lync Server route will be replaced by the voice route being imported.

    Import-CsLegacyConfiguration -ReplaceExisting

</div>

</div>

<div>

## Detailed Description

The **Import-CsLegacyConfiguration** cmdlet is used in conjunction with the **Merge-CsLegacyTopology** cmdlet to enable organizations to migrate from a previous version of Office Communications Server (either Office Communications Server 2007 R2 or Office Communications Server 2007) to Lync Server. The **Import-CsLegacyConfiguration** cmdlet is used to import voice policies; location profiles (for instance, dial plans); voice routes; voice normalization rules; meeting policies; external access policies; archiving policies; presence policies; Communicator Web Access URL settings; and dial-in conferencing access numbers.

Before you can run the **Import-CsLegacyConfiguration** cmdlet, you must first install the Windows Management Instrumentation (WMI) Backward Compatibility interfaces package; this application is installed by running OCSWMIBC.msi. After installing the Compatibility interfaces package, you should next run the **Merge-CsLegacyTopology** cmdlet. When the **Merge-CsLegacyTopology** cmdlet finishes, you should publish the merged topology by using Topology Builder. After publishing the merged topology, you can then call the **Import-CsLegacyConfiguration** cmdlet. The **Import-CsLegacyConfiguration** cmdlet uses WMI to read legacy data from the earlier version of Office Communications Server. The **Import-CsLegacyConfiguration** cmdlet then takes the retrieved data and creates corresponding objects in Lync Server. For example, for each voice policy found in your installation of Office Communications Server, a corresponding voice policy will be created in your new installation of Lync Server.

The **Import-CsLegacyConfiguration** cmdlet should be re-run whenever you make changes to any of the following Office Communications Server items: voice policies; location profiles; voice routes; voice normalization rules; meeting policies; external access policies; archiving policies; presence policies; Communicator Web Access URL settings; and dial-in conferencing access numbers. By default, only new items added to your Office Communications Server topology will be imported when you re-run the **Import-CsLegacyConfiguration** cmdlet. To import modified objects you must do two things. First, confirm that no changes have been made to the corresponding item (for example, a voice policy) in the Lync Server copy of the configuration. Second, run the **Import-CsLegacyConfiguration** cmdlet along with the ReplaceExisting parameter; this causes the **Import-CsLegacyConfiguration** cmdlet to import modified objects and to overwrite the corresponding object currently in Lync Server. Note that objects deleted from the Communications Server 2007 R2 topology do not result in corresponding deletions in Lync Server. You will need to manually remove those in Lync Server.

It’s important to know that the **Move-CsLegacyUser** cmdlet relies on information imported by the **Import-CsLegacyConfiguration** cmdlet. That means that, when running the **Move-CsLegacyUser** cmdlet, you might receive an error message telling you that you must run the **Import-CsLegacyConfiguration** cmdlet before proceeding. If that happens you must re-run the **Import-CsLegacyConfiguration** cmdlet before you will be able to move the legacy user.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Import-CsLegacyConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Import-CsLegacyConfiguration"}

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
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>ReplaceExisting</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>If present, this parameter instructs the <strong>Import-CsLegacyConfiguration</strong> cmdlet to overwrite any previously imported policies or settings that have changed since the last time the cmdlet was run.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report &quot;C:\Logs\ImportConfiguration.html&quot;</p></td>
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

None. The **Import-CsLegacyConfiguration** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Import-CsLegacyConfiguration** cmdlet does not return any objects or values.

</div>

<div>

## See Also


[Import-CsLegacyConferenceDirectory](import-cslegacyconferencedirectory.md)  
[Merge-CsLegacyTopology](merge-cslegacytopology.md)  
[Move-CsLegacyUser](move-cslegacyuser.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

