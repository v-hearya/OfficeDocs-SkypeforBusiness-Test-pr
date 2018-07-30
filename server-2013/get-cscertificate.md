---
title: Get-CsCertificate
TOCTitle: Get-CsCertificate
ms:assetid: 15b8f019-1d00-4389-9abe-18deb8cbf2ea
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398227(v=OCS.15)
ms:contentKeyID: 48183499
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsCertificate

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Returns information about certificates on the local computers that have been configured for use with Lync Server. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsCertificate [-Identity <XdsIdentity>] [-Report <String>] [-Type <CertType[]>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 returns information about the certificates currently assigned to Lync Server components. This is done by calling the **Get-CsCertificate** cmdlet without any additional parameters.

    Get-CsCertificate

</div>

<div>

## EXAMPLE 2

Example 2 retrieves all the Lync Server certificates used for internal Web services. To do this, the Type parameter is included, along with the parameter value WebServicesInternal.

    Get-CsCertificate -Type WebServicesInternal

</div>

<div>

## EXAMPLE 3

Example 3 returns all the Lync Server certificates that expire before September 1, 2012. To carry out this task, the command first uses the **Get-CsCertificate** cmdlet to return a collection of all the Lync Server certificates currently in use. This collection is then piped to the **Where-Object** cmdlet, which selects only those certificates that expire before September 1, 2012. The date specified in this example (9/1/2012) uses the U.S. English format for date-time values. Dates should be specified using a format compatible with your Regional and Language Options.

    Get-CsCertificate | Where-Object {$_.NotAfter -lt "9/1/2012"}

</div>

<div>

## EXAMPLE 4

Example 4 returns information about all the Lync Server certificates issued by the certification authority (CA) MyCa. To do this, the command first calls the **Get-CsCertificate** cmdlet without any parameters in order to return a collection of all the certificates currently in use. This collection is then piped to the **Where-Object** cmdlet, which picks out all the certificates where the Issuer property is equal to (-eq) "Cn=MyCa".

    Get-CsCertificate | Where-Object {$_.Issuer -eq "Cn=MyCa"}

</div>

<div>

## EXAMPLE 5

The command shown in Example 5 returns all the Lync Server certificates where the Subject property has been set to CN=atl-cs-001.litwareinc.com. This is done by using the **Get-CsCertificate** cmdlet to return a collection of all the Lync Server certificates, then piping that collection to the **Where-Object** cmdlet. In turn, the **Where-Object** cmdlet selects only those certificates where the Subject property is equal to "CN=atl-cs-001.litwareinc.com".

    Get-CsCertificate | Where-Object {$_.Subject -eq "CN=atl-cs-001.litwareinc.com"}

</div>

</div>

<div>

## Detailed Description

Lync Server uses certificates as a way for servers and server roles to verify their identities; for example, an Edge Server uses certificates to verify that the computer it is communicating with really is a Front End Server, and vice versa. In order to fully implement Lync Server you will need to have the appropriate certificates assigned to the appropriate server roles.

The **Get-CsCertificate** cmdlet provides a way for you to retrieve detailed information about the certificates that have been configured for use with Lync Server. Note that the cmdlet only returns information about Lync Server certificates. If a certificate has not been configured for use with Lync Server (by using the **Set-CsCertificate** cmdlet) then that certificate will not be returned when you run the **Get-CsCertificate** cmdlet.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsCertificate** cmdlet locally: RTCUniversalServerAdmins.

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
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Enables you to retrieve certificates configured at the global scope (global certificates are copied and distributed to the appropriate computers). Use this syntax to return information about the global certificates:</p>
<p>Get-CsCertificate –Identity &quot;global&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to record detailed information about the procedures carried out by the <strong>Get-CsCertificate</strong> cmdlet. The parameter value should be the full path to the HTML file that will be generated; for example: -Report C:\Logs\Certificates.html. If the specified file already exists, it will automatically be overwritten with the new information.</p></td>
</tr>
<tr class="odd">
<td><p><em>Type</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.CertType[]</p></td>
<td><p>Type of certificate being requested. Certificate types include, but are not limited to, the following:</p>
<p>AccessEdgeExternal</p>
<p>AudioVideoAuthentication</p>
<p>DataEdgeExternal</p>
<p>Default</p>
<p>External</p>
<p>Internal</p>
<p>iPhoneAPNService</p>
<p>iPadAPNService</p>
<p>MPNService</p>
<p>PICWebService (Microsoft Lync Online 2010 only)</p>
<p>ProvisionService (Microsoft Lync Online 2010 only)</p>
<p>WebServicesExternal</p>
<p>WebServicesInternal</p>
<p>WsFedTokenTransfer</p>
<p>For example, this syntax returns information about the Default certificate: -Type Default.</p>
<p>You can specify multiple types in a single command by separating the certificate types with commas:</p>
<p>-Type Internal,External,Default</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Get-CsCertificate** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Get-CsCertificate** cmdlet returns instances of the Microsoft.Rtc.Management.Deployment.CertificateReference object.

</div>

<div>

## See Also


[Import-CsCertificate](import-cscertificate.md)  
[Remove-CsCertificate](remove-cscertificate.md)  
[Request-CsCertificate](request-cscertificate.md)  
[Set-CsCertificate](set-cscertificate.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

