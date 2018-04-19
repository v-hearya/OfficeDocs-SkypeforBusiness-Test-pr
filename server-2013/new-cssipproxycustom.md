---
title: New-CsSipProxyCustom
TOCTitle: New-CsSipProxyCustom
ms:assetid: 3dc75cb0-c3d2-48bd-af32-2b2034b655dd
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425904(v=OCS.15)
ms:contentKeyID: 48183934
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsSipProxyCustom

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Used to assign a custom realm (SIP Communications Service) to a collection of proxy configuration settings. Realms (also known as protection domains) are used to authenticate user credentials during logon. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    New-CsSipProxyCustom -CustomValue <String>

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 assigns a custom realm (Litwareinc Communications Service) to a variable named $x.

    $x = New-CsSipProxyCustom -CustomValue "Litwareinc Communications Service"

</div>

</div>

<div>

## Detailed Description

Each proxy server must be associated with a realm; realms (also known as protection domains) indicate where a user’s logon credentials should be processed. By default, Lync Server uses SIP Communications Service as its default realm; however, it is possible to change the realm used by a proxy server. This is done by creating a SipProxy.Custom object and then assigning that object to the Realm property of the appropriate proxy server (or servers). You can create a custom realm by using the **New-CsSipProxyCustom** cmdlet.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **New-CsSipProxyCustom** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsSipProxyCustom"}

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
<td><p><em>CustomValue</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Name of the realm to be used for authentication purposes.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **New-CsSipProxyCustom** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **New-CsSipProxyCustom** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.Custom object.

</div>

<div>

## See Also


[New-CsSipProxyRealm](new-cssipproxyrealm.md)  
[New-CsSipProxyUseDefault](new-cssipproxyusedefault.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

