---
title: Get-CsPinPolicy
TOCTitle: Get-CsPinPolicy
ms:assetid: 1d627ba5-6333-466c-82a1-859deaf8d690
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398262(v=OCS.15)
ms:contentKeyID: 48183566
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsPinPolicy

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-06-04_

Returns information about the client personal identification number (PIN) policies configured for use in your organization. PIN authentication enables users to access Lync Server by providing a PIN instead of a user name and password. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsPinPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsPinPolicy [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 returns a collection of all the PIN policies configured for use in the organization. Calling the **Get-CsPinPolicy** cmdlet without any parameters always returns the complete set of PIN policies.

    Get-CsPinPolicy

</div>

<div>

## EXAMPLE 2

Example 2 returns a single PIN policy: the policy with the Identity site:Redmond.

    Get-CsPinPolicy -Identity "site:Redmond"

</div>

<div>

## EXAMPLE 3

The command shown in Example 3 uses the Filter parameter to return all the policies that have been configured at the per-user scope. This is done by using the filter value "tag:\*"; this value instructs the **Get-CsPinPolicy** cmdlet to return only those policies that have an Identity that begins with the characters "tag:".

    Get-CsPinPolicy -Filter "tag:*"

</div>

<div>

## EXAMPLE 4

Example 4 returns all the PIN policies where the AllowCommonPatterns property is True. In this example, the **Get-CsPinPolicy** cmdlet is first called without any additional parameters; that returns a collection of all the PIN policies configured for use in the organization. That collection is then passed to the **Where-Object** cmdlet, which picks out only those policies where the AllowCommonPatterns property is equal to True.

    Get-CsPinPolicy | Where-Object {$_.AllowCommonPatterns -eq $True}

</div>

<div>

## EXAMPLE 5

Like Example 4, the command shown in Example 5 uses the **Where-Object** cmdlet to return a subset of the existing PIN policies. In this case, the **Where-Object** cmdlet retrieves only those policies where the PinLifetime property is greater than 30. That means only policies that have PIN expiration times of more than 30 days will be returned.

    Get-CsPinPolicy | Where-Object {$_.PinLifetime -gt 30}

</div>

</div>

<div>

## Detailed Description

Lync Server enables users to connect to the system, or to join public switched telephone network (PSTN) conferences via telephone. Typically, logging on to the system or joining a conference requires the user to enter a user name or password; unfortunately, entering a user name and password can be a problem if you are using a phone that does not have an alphanumeric keypad. Because of that, Lync Server enables you to supply users with numeric-only PINs; when prompted, users can then log on to the system or join a conference by entering the PIN instead of a user name and password.

Lync Server uses PIN policies to manage PIN authentication properties; for example, you can specify the minimum length for a PIN and determine whether you will allow PINs that use "common patterns" such as consecutive digits (for example, a PIN like 123456). You can use the **Get-CsPinPolicy** cmdlet to retrieve information about the PIN policies currently configured for use in your organization.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsPinPolicy** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsPinPolicy"}

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
<td><p>Enables you to do a wildcard search for PIN policies. For example, to find all the policies configured at the site scope, use this Filter: site:*. To find the site policies Seattle, Seville, and Saskatoon (all of which start with the letter &quot;S&quot;) use this Filter: site:S*. Note that this parameter can only filter on the Identity property.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Unique identity assigned to the policy when it was created. PIN policies can be assigned at the global, site, or per-user scope. To refer to the global instance, use this syntax: -Identity global. To refer to a policy at the site scope, use this syntax: -Identity site:Redmond. To refer to a policy at the per-user scope, use syntax similar to this: -Identity RedmondPolicy.</p>
<p>Wildcard characters such as the asterisk (*) cannot be used with the Identity parameter. To do a wildcard search for policies, use the Filter parameter instead.</p>
<p>If neither the Identity nor the Filter parameter is specified the <strong>Get-CsPinPolicy</strong> cmdlet returns information about all the PIN policies configured for use in your organization.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the PIN policy data from the local replica of the Central Management store rather than from the Central Management store itself.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Get-CsPinPolicy** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Get-CsPinPolicy** cmdlet returns one or more instances of the Microsoft.Rtc.Management.WritableConfig.Policy.UserPin.UserPinPolicy object.

</div>

<div>

## See Also


[Grant-CsPinPolicy](grant-cspinpolicy.md)  
[New-CsPinPolicy](new-cspinpolicy.md)  
[Remove-CsPinPolicy](remove-cspinpolicy.md)  
[Set-CsPinPolicy](set-cspinpolicy.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

