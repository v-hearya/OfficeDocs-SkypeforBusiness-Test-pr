---
title: Test-CsCertificateConfiguration
TOCTitle: Test-CsCertificateConfiguration
ms:assetid: 8086bdf7-d283-4666-9f6c-0d5a3a31b3a6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398647(v=OCS.15)
ms:contentKeyID: 48184656
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Test-CsCertificateConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-07_

Returns information about the Lync Server certificates being used on the local computer. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Test-CsCertificateConfiguration [-Report <String>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 returns information about the certificates that are currently being used (on the local computer) by Lync Server.

    Test-CsCertificateConfiguration

</div>

<div>

## EXAMPLE 2

The command shown in Example 2 is a variation of the command shown in Example 1. In this case, however, the Report parameter is used to specify a file path (C:\\Logs\\Certificates.xml) for the output file generated when you run the **Test-CsCertificateConfiguration** cmdlet.

    Test-CsCertificateConfiguration -Report "C:\Logs\Certificates.xml"

</div>

</div>

<div>

## Detailed Description

The **Test-CsCertificateConfiguration** cmdlet is an example of a "synthetic transaction." Synthetic transactions are used in Lync Server to verify that users are able to successfully complete common tasks such as logging on to the system, exchanging instant messages, or making calls to a phone located on the public switched telephone network (PSTN). These tests can be conducted manually by an administrator, or they can be automatically run by an application such as Microsoft System Center Operations Manager (formerly Microsoft Operations Manager).

The **Test-CsCertificateConfiguration** cmdlet returns information about the certificates being used by Lync Server. The **Test-CsCertificateConfiguration** cmdlet is primarily intended for use by the Certificate wizard. It is recommended that administrators use the **Get-CsCertificate** cmdlet to retrieve certificate information.

Who can run this cmdlet: To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsCertificateConfiguration"}

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
<td><p><em>Report</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report &quot;C:\Logs\Certificates.html&quot;. If this file already exists, it will be overwritten when you run the cmdlet.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Test-CsCertificateConfiguration** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Test-CsCertificateConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.Deployment,CertificateExists object.

</div>

<div>

## See Also


[Get-CsCertificate](get-cscertificate.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

