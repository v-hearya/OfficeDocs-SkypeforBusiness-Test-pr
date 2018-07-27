---
title: Test-CsSetupPermission
TOCTitle: Test-CsSetupPermission
ms:assetid: 604ccb97-278a-4588-9ab8-991aaabae275
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398428(v=OCS.15)
ms:contentKeyID: 48184310
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Test-CsSetupPermission

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Verifies that the required permissions needed to install Lync Server or one of its components have been configured on the specified Active Directory container. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Test-CsSetupPermission -ComputerOU <String> [-Domain <Fqdn>] [-DomainController <Fqdn>] [-GlobalCatalog <Fqdn>] [-Report <String>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 checks to see if the required setup permissions have been applied to the CsServers OU in the litwareinc.com domain.

    Test-CsSetupPermission -ComputerOU "ou=CsServers,dc=litwareinc,dc=com"

</div>

</div>

<div>

## Detailed Description

The domain preparation that takes place when you install Lync Server does not automatically add the permissions that enable members of the RTCUniversalServerAdmins group to run the **Enable-CsTopology** cmdlet. That means that, by default, you must be a domain administrator in order to enable a topology. To give members of the RTCUniversalServerAdmins group the right to enable a topology, you must run the **Grant-CsSetupPermissions** cmdlet. In addition, you will need to run this cmdlet against each Active Directory container that houses computers running Lync Server.

The **Test-CsSetupPermission** cmdlet enables you to determine whether or not the requisite permissions have been added to a given Active Directory container (that is, a container hosting computers running Lync Server). The **Test-CsSetupPermission** cmdlet returns True if the correct permissions have been applied, and returns False if the correct permissions have not been applied. If the cmdlet returns False, you will need to run the **Grant-CsSetupPermission** cmdlet in order to make the necessary changes to the Active Directory container.

Who can run this cmdlet: To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsSetupPermission"}

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
<td><p><em>ComputerOU</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Distinguished name of the organizational unit (OU) that contains the accounts for the computers running Lync Server. For example: &quot;ou=CsServers,dc=litwareinc,dc=com&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Domain</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Name of the domain where the OU to be checked is located. If this parameter is not included, then the <strong>Test-CsSetupPermission</strong> cmdlet will look for the OU in the current domain.</p></td>
</tr>
<tr class="odd">
<td><p><em>DomainController</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Fully qualified domain name (FQDN) of a domain controller in your domain. This parameter is not required if you are running the <strong>Test-CsSetupPermission</strong> cmdlet on a computer with an account in your domain.</p></td>
</tr>
<tr class="even">
<td><p><em>GlobalCatalog</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>FQDN of a global catalog server in your domain. This parameter is not required if you are running the <strong>Test-CsSetupPermission</strong> cmdlet on a computer with an account in your domain.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Reports detailed activity to the screen as the cmdlet runs.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Test-CsSetupPermission** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Test-CsSetupPermission** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.

</div>

<div>

## See Also


[Grant-CsSetupPermission](grant-cssetuppermission.md)  
[Revoke-CsSetupPermission](revoke-cssetuppermission.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

