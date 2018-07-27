---
title: Update-CsUserData
TOCTitle: Update-CsUserData
ms:assetid: e3cb48e9-9b5e-4c73-ab54-4aea16533ed8
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205358(v=OCS.15)
ms:contentKeyID: 48185720
ms.date: 07/07/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Update-CsUserData

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-07-01_

Uses previously-exported user information to update Lync Server user data. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Update-CsUserData -FileName <String> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-RoutingGroupFilter <String>] [-UserFilter <String>] [-WhatIf [<SwitchParameter>]]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 updates Lync Server user data based on information stored in the file C:\\Logs\\ExportedUserData.zip.

    Update-CsUserData -Filename "C:\Logs\ExportedUserData.zip"

</div>

<div>

## Example 2

In Example 2, user data is updated for a single user: the user with the SIP address kenmyer@litwareinc.com. This is done by including the UserFilter parameter followed by the user’s SIP address (minus the sip: prefix).

    Update-CsUserData -Filename "C:\Logs\ExportedUserData.zip" -UserFilter "kenmyer@litwareinc.com"

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The **Update-CsUserData** cmdlet enables administrators to update user data for a specified user or set of users. (Note that this data must have previously been exported by using the [Export-CsUserData](export-csuserdata.md) cmdlet.) This updating is typically done in order to restore lost data to a logged-on user.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Update-CsUserData"}

**Lync Server Control Panel:** The functions carried out by the **Update-CsUserData** cmdlet are not available in the Lync Server Control Panel.

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
<td><p>Full path to the .ZIP file or .XML file containing the user data to be updated. For example:</p>
<p>-FileName “C:\Data\Lync2010.zip&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>DomainController</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Enables administrators to specify the FQDN of the domain controller to be used when running the <strong>Update-CsUserData</strong> cmdlet. If not specified, the cmdlet will use the first available domain controller.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>RoutingGroupFilter</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to update data only for the specified routing groups. Routing groups are used to indicate the Front End server that users register with.</p></td>
</tr>
<tr class="even">
<td><p><em>UserFilter</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to update data for a single user. That user specified by using his or her SIP address, minus the sip: prefix. For example:</p>
<p>-UserFilter &quot;kenmyer@litwareinc.com&quot;</p></td>
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

<span id="InputTypes"></span>

<div>

## Input Types

None. The **Update-CsUserData** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **Update-CsUserData** cmdlet updates Lync Server user information.

</div>

<div>

## See Also


[Convert-CsUserData](convert-csuserdata.md)  
[Export-CsUserData](export-csuserdata.md)  
[Import-CsUserData](import-csuserdata.md)  
[Sync-CsUserData](sync-csuserdata.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

