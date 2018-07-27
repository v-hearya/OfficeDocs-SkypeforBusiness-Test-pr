---
title: Get-CsCpsConfiguration
TOCTitle: Get-CsCpsConfiguration
ms:assetid: d81ee8fe-d02b-4f60-a4d5-6aa84f65d156
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398948(v=OCS.15)
ms:contentKeyID: 48185473
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsCpsConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Returns information about the Call Park service. Call parking is a service that allows a user to "park" an incoming phone call. Parking a call transfers it to a number in a specified range, or orbit, and then immediately places the call on hold. Anyone (not just the person who originally answered the call) can resume the conversation from any telephone in the system by entering the correct number. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsCpsConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsCpsConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 retrieves a collection of all the Call Park service configurations that have been defined for use in your organization.

    Get-CsCpsConfiguration

</div>

<div>

## EXAMPLE 2

Example 2 retrieves only the Call Park service configurations with the Identity site:Redmond1.

    Get-CsCpsConfiguration -Identity site:Redmond1

</div>

<div>

## EXAMPLE 3

In Example 3, the Filter parameter is used to return all the Call Park service configurations that have been configured at the site scope. The wildcard string site:\* tells the **Get-CsCpsConfiguration** cmdlet to return only those settings where the Identity begins with the string value site:.

    Get-CsCpsConfiguration -Filter site:*

</div>

<div>

## EXAMPLE 4

As in Example 3, in this example we use the Filter parameter to retrieve a subset of all the defined Call Park service configurations. In this case, we filter on the string \*:re\*, which will return Call Park configurations for all sites with names beginning with the letters re, such as Redmond1, Redmond2, and RemoteComputer.

    Get-CsCpsConfiguration -Filter *:re*

</div>

<div>

## EXAMPLE 5

Example 5 returns all the Call Park service settings that do not play music when a caller is placed on hold. To do this, the command first uses the **Get-CsCpsConfiguration** cmdlet to retrieve all the Call Park service settings configured for use in the organization. That collection is then piped to the **Where-Object** cmdlet, which, in turn, applies a filter that limits the returned data to those items where the EnableMusicOnHold property is equal to (-eq) False.

    Get-CsCpsConfiguration | Where-Object {$_.EnableMusicOnHold -eq $False}

</div>

</div>

<div>

## Detailed Description

This cmdlet is used to retrieve one or more Call Park service configurations. A Call Park service configuration specifies what happens to a call once it’s parked. For example, if a parked call isn’t answered after a period of time it can be automatically forwarded to someone else, such as an administrator, or to a Response Group. Calls can also be configured to ring after a certain period of time to ensure the call isn’t forgotten. In addition, Call Park service can be configured to play music on hold to the caller while the call is parked.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsCpsConfiguration** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsCpsConfiguration"}

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
<td><p>Allows you to do a wildcard search to retrieve only those configurations with Identity values matching the wildcard string.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>The unique identifier of the Call Park service configuration you want to retrieve. This identifier will be either Global or site:&lt;sitename&gt;, where &lt;sitename&gt; is the name of the site to which the configuration applies.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the Call Park service information from the local replica of the Central Management store, rather than the Central Management store itself.</p></td>
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

Retrieves one or more objects of type Microsoft.Rtc.Management.WritableConfig.Settings.CallParkServiceSettings.CallParkServiceSettings.

</div>

<div>

## See Also


[New-CsCpsConfiguration](new-cscpsconfiguration.md)  
[Remove-CsCpsConfiguration](remove-cscpsconfiguration.md)  
[Set-CsCpsConfiguration](set-cscpsconfiguration.md)  
[Set-CsCallParkServiceMusicOnHoldFile](set-cscallparkservicemusiconholdfile.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

