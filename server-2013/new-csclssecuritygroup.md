---
title: New-CsClsSecurityGroup
TOCTitle: New-CsClsSecurityGroup
ms:assetid: e42f2d5f-7720-4b69-8563-48172120d8d9
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205359(v=OCS.15)
ms:contentKeyID: 48185725
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsClsSecurityGroup

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Creates a new centralized logging configuration security group. Centralized logging provides a way for administrators to simultaneously enable or disable event tracing on multiple computers. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    New-CsClsSecurityGroup -Name <String> -Parent <String> <COMMON PARAMETERS>

    New-CsClsSecurityGroup -Identity <XdsIdentity> <COMMON PARAMETERS>

    COMMON PARAMETERS: -AccessLevel <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The command shown in Example 1 creates a new centralized logging security group with the Identity global/HelpDesk. In this example, the AccessLevel property is set to Tier3.

    New-CsClsSecurityGroup -Identity "global/HelpDesk" -AccessLevel "Tier3"

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The centralized logging service (which replaces the OCSLogger and OCSTracer tools used in Microsoft Lync Server 2010) provides a way for administrators to manage logging and tracing for all computers and pools running Lync Server 2013. Centralized logging enables administrators to stop, start, and configure logging for one or more pools and computers by using a single command; for example, you can use one command to enable Address Book service logging on all your Address Book servers. This differs from the OCSLogger and OCSTracer tools, which had to be individually managed (including individually stopped and started) on each server. In addition, the centralized logging service also provides a way for administrators to search trace logs from the command, using the Windows PowerShell command-line interface and the [Search-CsClsLogging](search-csclslogging.md) cmdlet.

With Lync Online, security groups are used to determine which users have access to the personally-identifiable information that is written to the log files. Security groups are created by using the New-CsClsSecurityGroup cmdlet and then are added to a collection of centralized logging configuration settings.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsClsSecurityGroup"}

**Lync Server Control Panel:** The functions carried out by the **New-CsClsSecurityGroup** cmdlet are not available in the Lync Server Control Panel.

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
<td><p><em>AccessLevel</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>String value specifying the access level assigned to the group. Access levels are arbitrary string values assigned by administrators and used to categorize security groups. For example:</p>
<p>-AccessLevel &quot;Tier3&quot;</p>
<p>Multiple groups can share the same access level. Currently the only values that have meaning are &quot;Tier3&quot;, &quot;Tier2&quot;, &quot;Product&quot;, &quot;Ops&quot;, and &quot;Pii&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Unique identifier for the new security group. Security group Identities consist of the centralized logging configuration scope where the group will be created plus a unique security group name. For example, to create a global security group named HelpDesk use this syntax:</p>
<p>-Identity &quot;global/HelpDesk&quot;</p>
<p>If you use the Identity parameter then you cannot use either the name parameter or the Parent parameter in that same command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Name</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Unique name for the new security group. For example:</p>
<p>-Name &quot;HelpDesk&quot;</p>
<p>If you use the Name parameter you must also use the Parent parameter. However, you should not use the Identity parameter in the same command as the Name and Parent parameters.</p></td>
</tr>
<tr class="even">
<td><p><em>Parent</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Scope of the centralized logging configuration settings where the new security group will be located. For example, to add the new security group to the global settings, use this syntax:</p>
<p>-Parent &quot;global&quot;</p>
<p>You can return identities for all your centralizing logging &quot;parents&quot; by using this command:</p>
<p>Get-CsCentralizedLoggingConfiguration | Select-Object Identity</p>
<p>If you use the Name parameter you must also use the Parent parameter. However, you should not use the Identity parameter in the same command as the Name and Parent parameters.</p></td>
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
<td><p><em>InMemory</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet’s matching Set- cmdlet.</p></td>
</tr>
<tr class="even">
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

None. The **New-CsClsSecurityGroup** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **New-CsClsSecurityGroup** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.SecurityGroup\#Decorated object.

</div>

<div>

## See Also


[Get-CsClsSecurityGroup](get-csclssecuritygroup.md)  
[Remove-CsClsSecurityGroup](remove-csclssecuritygroup.md)  
[Set-CsClsSecurityGroup](set-csclssecuritygroup.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

