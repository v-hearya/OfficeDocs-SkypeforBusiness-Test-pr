---
title: Get-CsWebServiceConfiguration
TOCTitle: Get-CsWebServiceConfiguration
ms:assetid: 28582668-839c-4b04-8211-928c91634672
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425751(v=OCS.15)
ms:contentKeyID: 48183687
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsWebServiceConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

Returns information about all the Web Services configuration settings in use in your organization. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsWebServiceConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsWebServiceConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 returns information about all the Web Services configuration settings currently in use in the organization.

    Get-CsWebServiceConfiguration

</div>

<div>

## EXAMPLE 2

The command shown in Example 2 returns information about the Web Services configuration settings that have the Identity site:Redmond.

    Get-CsWebServiceConfiguration -Identity site:Redmond

</div>

<div>

## EXAMPLE 3

Example 3 returns all the Web Services configuration settings that have been assigned at the site scope. To do this, the Filter parameter is included when calling the **Get-CsWebServiceConfiguration** cmdlet; the filter value "site:\*" ensures that only those settings that have an Identity that begins with the string value "site:" are returned.

    Get-CsWebServiceConfiguration -Filter "site:*"

</div>

<div>

## EXAMPLE 4

In Example 4, the command returns all the Web Services configuration settings that do not allow personal identification number (PIN) authentication. This is done by first calling the **Get-CsWebServiceConfiguration** cmdlet to return all the Web Services configuration settings currently in use. This collection is then piped to the **Where-Object** cmdlet, which picks out only those settings where the UsePinAuth property is equal to False.

    Get-CsWebServiceConfiguration | Where-Object {$_.UsePinAuth -eq $False}

</div>

<div>

## EXAMPLE 5

Example 5 returns all the Web Services configuration settings where the maximum group expansion size is greater than 100. To do this, the command first uses the **Get-CsWebServiceConfiguration** cmdlet to return all the Web Services configuration settings currently in use. This information is then piped to the **Where-Object** cmdlet, which selects only those settings where the MaxGroupSizeToExpand property is greater than 100.

    Get-CsWebServiceConfiguration | Where-Object {$_.MaxGroupSizeToExpand -gt 100}

</div>

</div>

<div>

## Detailed Description

Many Lync Server components are web-based: these components either use web services or webpages to carry out their tasks. For example, users employ a web service when searching for new contacts in the Address Book or when using group expansion to view the individual members of a distribution group. Likewise, components ranging from dial-in conferencing to Lync Server Control Panel use webpages as the interface between Lync Server and users.

The **CsWebServiceConfiguration** cmdlets enable administrators to manage Web Services configuration settings throughout the organization; this includes managing group expansion, certificate settings, and allowed authentication methods. Because you can configure different settings at the global, site, and service scope (albeit for the only the Web Services service), you can customize Web Services capabilities for different users and different locations.

The **Get-CsWebServiceConfiguration** cmdlet enables you to return detailed information about the Web Services configuration settings currently in use in your organization.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsWebServiceConfiguration** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsWebServiceConfiguration"}

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
<td><p><em>Filter</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to use wildcards when specifying the Web Services configuration settings collection (or collections) to be returned. For example, this syntax returns all the settings configured at the site scope: -Filter &quot;site:*&quot;.</p>
<p>You cannot use both the Filter and the Identity parameters in the same command.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Unique identifier for the Web Services configuration settings to be returned. To return the global settings, use this syntax: -Identity global. To return settings configured at the site scope, use syntax similar to this: -Identity &quot;site:Redmond.&quot; Service-scope settings can be returned using syntax like this: -Identity &quot;service:WebServer:atl-cs-001.litwareinc.com&quot;.</p>
<p>You cannot use both the Filter and the Identity parameters in the same command. If you do not specify either parameter, the <strong>Get-CsWebServiceConfiguration</strong> cmdlet will return all the Web Services settings collections currently in use in your organization.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the Web Services configuration data from the local replica of the Central Management store rather than from the Central Management store itself.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Get-CsWebServiceConfiguration** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Get-CsWebServiceConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Web.WebServiceSettings object.

</div>

<div>

## See Also


[New-CsWebServiceConfiguration](new-cswebserviceconfiguration.md)  
[Remove-CsWebServiceConfiguration](remove-cswebserviceconfiguration.md)  
[Set-CsWebServiceConfiguration](set-cswebserviceconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

