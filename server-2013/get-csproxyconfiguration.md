---
title: Get-CsProxyConfiguration
TOCTitle: Get-CsProxyConfiguration
ms:assetid: e4836619-026f-4df0-adbd-aa5216e36368
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg399011(v=OCS.15)
ms:contentKeyID: 48185728
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsProxyConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-07_

Returns information about the proxy server configuration settings currently in use in your organization. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsProxyConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsProxyConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 returns a collection of all the proxy configuration settings currently in use in the organization. This is done by calling the **Get-CsProxyConfiguration** cmdlet without any parameters.

    Get-CsProxyConfiguration

</div>

<div>

## EXAMPLE 2

In Example 2, information about the proxy configuration settings that have the Identity service:EdgeServer:atl-cs-001.litwareinc.com is returned. Because Identities must be unique, this command will never return more than one collection of settings.

    Get-CsProxyConfiguration -Identity "service:EdgeServer:atl-cs-001.litwareinc.com"

</div>

<div>

## EXAMPLE 3

Example 3 returns information about all of the proxy settings that have been configured at the service scope. To do this, the command calls the **Get-CsProxyConfiguration** cmdlet along with the Filter parameter; the filter value "service:\*" ensures that only those settings that have an Identity that begins with the string value "service:" will be returned.

    Get-CsProxyConfiguration -Filter "service:*"

</div>

<div>

## EXAMPLE 4

Example 4 returns information about the proxy configuration settings that do not allow the use of client certificates as an authentication mechanism. To carry out this task, the command first uses the **Get-CsProxyConfiguration** cmdlet to return a collection of all the proxy configuration settings currently in use. This collection is then piped to the **Where-Object** cmdlet, which selects only those settings where the UseCertificateForClientToProxyAuth property is equal to False.

    Get-CsProxyConfiguration | Where-Object {$_.UseCertificateForClientToProxyAuth -eq $False}

</div>

<div>

## EXAMPLE 5

Example 5 returns all the proxy configuration settings where the maximum body size for a client message is less than 5000 kilobytes. To do this, the command first calls the **Get-CsProxyConfiguration** cmdlet without any parameters; this returns a collection of all the proxy configuration settings currently in use. This collection is then piped to the **Where-Object** cmdlet, which picks out those settings where the MaxClientMessageBodySizeKb property is less than 5000 kilobytes.

    Get-CsProxyConfiguration | Where-Object {$_.MaxClientMessageBodySizeKb -lt 5000}

</div>

</div>

<div>

## Detailed Description

Lync Server enables you to manage your proxy servers through proxy server configuration settings. These settings, which can be applied at both the global scope and the service scope (albeit for only the Edge Server and Registrar services) enable you to control such things as the authentication protocols that can be used by client endpoints and whether or not compression will be used on incoming and outgoing proxy server connections. When you install Lync Server, a global collection of proxy server configuration settings is automatically created for you. As noted, you can also create additional collections at the service scope.

The **Get-CsProxyConfiguration** cmdlet enables you to return information about any of the proxy server configuration settings currently in use in your organization.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsProxyConfiguration** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsProxyConfiguration"}

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
<td><p>Enables you to use wildcards when specifying the proxy configuration settings to be returned. For example, this syntax returns all the settings configured at the service scope: -Filter &quot;service:*&quot;.</p>
<p>You cannot use both the Filter and the Identity parameters in the same command.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Unique identifier for the proxy server configuration settings to be returned. To return the global settings, use this syntax: -Identity global. To return settings configured at the service scope, use syntax similar to this: -Identity &quot;service:EdgeServer:atl-cs-001.litwareinc.com&quot;. Note that you cannot use wildcards when specifying an Identity. If you want to (or need to) use wildcards, use the Filter parameter instead.</p>
<p>If this parameter is not included, the <strong>Get-CsProxyConfiguration</strong> cmdlet returns all of the proxy server settings currently in use in your organization.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the proxy configuration data from the local replica of the Central Management store rather than from the Central Management store itself.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Get-CsProxyConfiguration** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Get-CsProxyConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.ProxySettings object.

</div>

<div>

## See Also


[New-CsProxyConfiguration](new-csproxyconfiguration.md)  
[Remove-CsProxyConfiguration](remove-csproxyconfiguration.md)  
[Set-CsProxyConfiguration](set-csproxyconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

