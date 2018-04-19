---
title: New-CsWebOrigin
TOCTitle: New-CsWebOrigin
ms:assetid: 16053a99-b5ff-45e1-be95-b04e3f2fe528
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ950236(v=OCS.15)
ms:contentKeyID: 51567732
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsWebOrigin

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-05-28_

Creates a new domain object that can be added to the collection of domains allowed to send cross-domain scripting requests to the Lync Server 2013 deployment.

This cmdlet was introduced in the Cumulative Updates for Lync Server 2013: February 2013.

<div>

## Syntax

    New-CsWebOrigin -Url <String>

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The commands shown in Example 1 add the domain http://fabrikam.com to a new collection of web service configuration settings being created for the Redmond site. To do this, the first command in the example uses the **New-CsWebOrigin** cmdlet to create a domain object for fabrikam.com. The resulting domain object is stored in a variable named $x.

The second command in the example uses the **New-CsWebServiceConfiguration** cmdlet to create the web service configuration settings for the Redmond site. The syntax "–CrossDomainAuthorizationList $x" adds http://fabrikam.com to the collection of domains authorized for cross-domain scripting.

    $x = New-CsWebOrigin -Url "http://fabrikam.com"
    New-CsWebServiceConfiguration -Identity "site:Redmond" - CrossDomainAuthorizationList $x

</div>

<div>

## Example 2

The commands shown in Example 2 add the domain http://fabrikam.com to an existing collection of web service configuration settings. To carry out this task, the first command in the example uses the **New-CsWebOrigin** cmdlet to create a domain object for fabrikam.com. The resulting domain object is stored in a variable named $x.

The second command in the example uses the **Set-CsWebServiceConfiguration** cmdlet to add http://fabrikam.com to the web service configuration settings applied to the Redmond site. The syntax @{Add=$x} adds the domain to any domains already in the collection of domains authorized for cross-domain scripting. To replace the existing collection with just http://fabrikam.com use the syntax @{Replace=$x}.

    $x = New-CsWebOrigin -Url "http://fabrikam.com"
    Set-CsWebServiceConfiguration -Identity "site:Redmond" - CrossDomainAuthorizationList @{Add=$x}

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The New-CsWebOrigin cmdlet is used to specify domains that are authorized to host web applications which, in turn, are permitted to send cross-domain scripting requests to your deployment of Lync Server 2013. This cmdlet is primarily used for applications created on top of the Unified Communications Web API.

To add a domain to a collection of web service configuration settings, you must first create a domain object by using the New-CsWebOrigin cmdlet. This domain object, which will exist only in memory, must be stored in a variable. After the object has been created, it can then be added to a collection of web service configuration settings by using either the New-CsWebServiceConfiguration cmdlet or the Set-CsWebServiceConfiguration cmdlet.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsWebOrigin"}

**Lync Server Control Panel:** The functions carried out by the **New-CsWebOrigin** cmdlet are not available in the Lync Server Control Panel.

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
<td><p><em>Url</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>URL of the domain authorized to send cross-domain scripting requests. URLs must be prefaced using either the http: or the https: prefix. For example:</p>
<p>-Url &quot;http://contoso.com&quot;</p></td>
</tr>
</tbody>
</table>


</div>

<span id="InputTypes"></span>

<div>

## Input Types

None. The **New-CsWebOrigin** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **New-CsWebOrigin** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Web.Origin object.

</div>

<div>

## See Also


[New-CsWebServiceConfiguration](new-cswebserviceconfiguration.md)  
[Set-CsWebServiceConfiguration](set-cswebserviceconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

