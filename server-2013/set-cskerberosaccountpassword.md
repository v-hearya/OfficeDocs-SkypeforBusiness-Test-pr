---
title: Set-CsKerberosAccountPassword
TOCTitle: Set-CsKerberosAccountPassword
ms:assetid: 837292b9-3c08-4c3c-a49d-3f9492518ddd
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398659(v=OCS.15)
ms:contentKeyID: 48184680
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsKerberosAccountPassword

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Locates each server running Web Services in a site that has been assigned a Kerberos account, and then updates the Internet Information Services (IIS) configuration settings on each of those servers. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsKerberosAccountPassword -UserAccount <String> <COMMON PARAMETERS>

    Set-CsKerberosAccountPassword -FromComputer <Fqdn> -ToComputer <Fqdn> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 sets the password for the Kerberos account litwareinc\\kerberostest.

    Set-CsKerberosAccountPassword -UserAccount "litwareinc\kerberostest"

</div>

<div>

## EXAMPLE 2

In Example 2, the Kerberos account password is copied from the computer atl-cs-001.litwareinc.com to the computer dublin-cs-001.litwareinc.com.

    Set-CsKerberosAccountPassword -FromComputer "atl-cs-001.litwareinc.com" -ToComputer "dublin-cs-001.litwareinc.com"

</div>

</div>

<div>

## Detailed Description

In Microsoft Office Communications Server 2007 and Microsoft Office Communications Server 2007 R2, IIS ran under a standard user account. This had the potential to cause issues: if that password expired you could lose your Web Services, an issue that was often difficult to diagnose. To help avoid the issue of expiring passwords, Lync Server enables you to create a computer account (for a computer that doesn’t actually exist) that can serve as the authentication principal for all the computers in a site that are running IIS. Because these accounts use the Kerberos authentication protocol, the accounts are referred to as Kerberos accounts, and the new authentication process is known as Kerberos web authentication. This enables you to manage all your IIS servers by using a single account.

To run your servers under this new authentication principal, you must first create a computer account by using the **New-CsKerberosAccount** cmdlet; this account is then assigned to one or more sites. After the assignment has been made, the association between the account and the Lync Server site is enabled by running the **Enable-CsTopology** cmdlet. Among other things, this creates the required service principal name (SPN) in Active Directory Domain Services. SPNs provide a way for client applications to locate a particular service.

After a new association has been made, the **Set-CsKerberosAccountPassword** cmdlet provides a way to modify the password assigned to the account and, equally important, update the password on every computer that uses the specified Kerberos test account for Kerberos web authentication.

In addition, the cmdlet can also use the ToComputer and FromComputer parameters to copy this configuration information from one computer to another.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsKerberosAccountPassword** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsKerberosAccountPassword"}

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
<td><p><em>FromComputer</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Fully qualified domain name (FQDN) of the computer containing the Kerberos account’s password that will be copied to another computer. This parameter cannot be used if you use the UserAccount parameter.</p></td>
</tr>
<tr class="even">
<td><p><em>ToComputer</em></p></td>
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>FQDN of the computer where the Kerberos account password will be copied. This parameter cannot be used if you use the UserAccount parameter.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserAccount</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Account name for the account whose password should be changed. This account name must use the format domain_name\user_name; for example: -UserAccount &quot;litwareinc\kerberostest&quot;.</p>
<p>Note that, despite the name UserAccount, the account is actually a computer account, not a user account.</p></td>
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
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report &quot;C:\Logs\SetKerberosPassword.html&quot;.</p></td>
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

None.

</div>

<div>

## Return Types

The **Set-CsKerberosAccountPassword** cmdlet does not return any objects or values. Instead, the cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.KerberosAccount.KerberosAccount object.

</div>

</div>

<span> </span>

</div>

</div>

</div>

