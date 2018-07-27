---
title: Remove-CsKerberosAccountAssignment
TOCTitle: Remove-CsKerberosAccountAssignment
ms:assetid: f878fed1-ee6d-4275-8f76-2bc134e465c2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg413052(v=OCS.15)
ms:contentKeyID: 48185875
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Remove-CsKerberosAccountAssignment

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Removes one or more Kerberos account assignments. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Remove-CsKerberosAccountAssignment -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The commands shown in Example 1 remove the Kerberos account assignment from the Redmond site, then call the **Enable-CsTopology** cmdlet to finish disabling Kerberos web authentication.

    Remove-CsKerberosAccountAssignment -Identity "site:Redmond"
    Enable-CsTopology

</div>

<div>

## EXAMPLE 2

In Example 2, all the Kerberos account assignments currently in use are deleted. To do this, the first command calls the **Get-CsKerberosAccountAssignment** cmdlet (without any parameters) in order to return a collection of all the Kerberos account assignments. This collection is then piped to the **Remove-CsKerberosAccountAssignment** cmdlet, which deletes each assignment in the collection. When that’s done, the second command in the example calls the **Enable-CsTopology** cmdlet to finish disabling Kerberos web authentication.

    Get-CsKerberosAccountAssignment | Remove-CsKerberosAccountAssignment
    Enable-CsTopology

</div>

</div>

<div>

## Detailed Description

In Microsoft Office Communications Server 2007 and Microsoft Office Communications Server 2007 R2, IIS ran under a standard user account. This had the potential to cause issues: if that password expired you could lose your Web Services, an issue that was often difficult to diagnose. To help avoid the issue of expiring passwords, Lync Server enables you to create a computer account (for a computer that doesn’t actually exist) that can serve as the authentication principal for all the computers in a site that are running IIS. Because these accounts use the Kerberos authentication protocol, the accounts are referred to as Kerberos accounts, and the new authentication process is known as Kerberos web authentication. This enables you to manage all your IIS servers by using a single account.

To run your servers under this new authentication principal, you must first create a computer account (which, again, is not tied to an actual computer) by using the **New-CsKerberosAccount** cmdlet; this account is then assigned to one or more sites. After the assignment has been made, the association is enabled by running the **Enable-CsTopology** cmdlet; among other things, this creates the required service principal name (SPN) in Active Directory Domain Services. SPNs provide a way for client applications to locate a particular service.

Each Lync Server site can be associated with, at most, a single Kerberos account. (However, each account can be associated with multiple sites.) At any time you can use the **Remove-CsKerberosAccountAssignment** cmdlet to remove the association between a site and an account. This cmdlet does not delete the account in question; it simply severs the association between the account and the site, effectively disabling Kerberos web authentication in that site.

Note that, after running the **Remove-CsKerberosAccountAssignment** cmdlet you must then run the **Enable-CsTopology** cmdlet. This removes the account’s service principal name from Active Directory, and complete disables Kerberos web authentication.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Remove-CsKerberosAccountAssignment** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsKerberosAccountAssignment"}

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
<td><p><em>Identity</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Unique identifier of the site where the Kerberos account assignment is to be removed. (This is the Identity of the site, not of the Kerberos account.) For example: -Identity &quot;site:Redmond&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>When present, suppresses all error messages except for fatal errors.</p></td>
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

<div>

## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.KerberosAccount.KerberosAccountAssignment object. The **Remove-CsKerberosAccountAssignment** cmdlet accepts pipelined instances of the Kerberos account assignment object.

</div>

<div>

## Return Types

None. The **Remove-CsKerberosAccountAssignment** cmdlet does not return any objects or values. Instead, the cmdlet deletes existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.KerberosAccount.KerberosAccountAssignment object.

</div>

<div>

## See Also


[Get-CsKerberosAccountAssignment](get-cskerberosaccountassignment.md)  
[New-CsKerberosAccountAssignment](new-cskerberosaccountassignment.md)  
[Set-CsKerberosAccountAssignment](set-cskerberosaccountassignment.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

