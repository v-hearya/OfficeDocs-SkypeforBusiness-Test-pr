---
title: Import-CsDeviceUpdate
TOCTitle: Import-CsDeviceUpdate
ms:assetid: cc2e5fab-d978-4e7e-8fc6-d12a0172c07c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398861(v=OCS.15)
ms:contentKeyID: 48185653
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Import-CsDeviceUpdate

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-05_

Imports a set of device update rules downloaded from the Microsoft website. Device update rules associate firmware version updates with hardware devices running Lync Phone Edition. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Import-CsDeviceUpdate -FileName <String> -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 imports device update rules from the file C:\\Updates\\UCUpdates.cab.

    Import-CsDeviceUpdate -Identity "service:WebServer:atl-cs-001.litwareinc.com" -FileName C:\Updates\UCUpdates.cab

</div>

<div>

## EXAMPLE 2

The command shown in Example 2 imports device update rules from the UNC path \\\\atl-fs-001\\Updates\\UCUpdates.cab.

    Import-CsDeviceUpdate -Identity "service:WebServer:atl-cs-001.litwareinc.com" -FileName \\atl-fs-001\Updates\UCUpdates.cab

</div>

<div>

## EXAMPLE 3

Example 3 shows how you can use a single command to import device update rules to all your servers running Web Services. To do this, the command first calls the **Get-CsService** cmdlet, along with the WebServer parameter, in order to return a collection of all of your servers running the Web Services service. This collection is then piped to the **ForEach-Object** cmdlet, which loops through each server in the collection and uses the **Import-CsDeviceUpdate** cmdlet to update the latest device update rules to those servers. Note that this command will work only if you have copied UCUpdates.cab to the same location (C:\\Updates) on all your servers.

    Get-CsService -WebServer | ForEach-Object {Import-CsDeviceUpdate -Identity $_.Identity -FileName C:\Updates\UCUpdates.cab}

</div>

</div>

<div>

## Detailed Description

Periodically, Microsoft releases a new set of device update rules for Lync Phone Edition. These rules represent firmware updates for devices that run Lync Phone Edition. After these rules have been imported, administrators can test the firmware updates and then, assuming the tests succeed, can make the updates available to all the relevant devices used in the organization.

The only way to create new update rules is to download update packs from Microsoft; you cannot create your own device update rules. To obtain the latest set of device update rules, go to the Help and Support page on the Microsoft website and search for "Phone Edition". Download the update package and extract the files to a folder on the computer where the updates are to be uploaded. After the files have been extracted, you can then use the **Import-CsDeviceUpdate** cmdlet to import the device update rules found in the extracted .CAB file (which will have the name UCUpdates.cab).

As noted, updates can only be loaded locally; you will need to copy UCUpdates.cab to any computer running the Web Services service that needs to host device update rules. Keep in mind as well that device update rules are not replicated from server-to-server. If you want all the device update rules throughout your organization to remain in sync you will need to perform the same operation on each server hosting these rules. For example, if you remove a rule from one Web Services server you will then need to remove that same rule from your other Web Services servers. Otherwise, your device update rules will no longer be in sync.

Update rules can only be imported to services; they are not applicable at the global, site, or per-user scopes. Note, however, that the **Import-CsDeviceUpdate** cmdlet does not automatically add rules and updates to every service in a site; instead, it loads those rules and updates only to the specified service. For example, if you have three servers in a site running Web Services, you will need to run the **Import-CsDeviceUpdate** cmdlet three times, one for each instance of Web Services. Alternatively, you can use a command like the one shown in Example 3; this one command retrieves the Identity of all your servers Web Services and then runs the **Import-CsDeviceUpdate** cmdlet against each of those servers.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Import-CsDeviceUpdate** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Import-CsDeviceUpdate"}

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
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Path to the update file (for example, C:\Updates\UCUpdates.cab).</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Indicates the service instance where the new update rules will be applied. For example: -Identity &quot;service:WebServer:atl-cs-001.litwareinc.com&quot;.</p>
<p>The Identity should be the fully qualified domain name of the Front End pool where the Web server is installed.</p></td>
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
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
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

None. The **Import-CsDeviceUpdate** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Import-CsDeviceUpdate** cmdlet imports instances of the Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.Rule class.

</div>

<div>

## See Also


[Get-CsDeviceUpdateRule](get-csdeviceupdaterule.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

