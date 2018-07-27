---
title: Enable-CsPublicProvider
TOCTitle: Enable-CsPublicProvider
ms:assetid: 98370dfd-9a53-41a8-a1f3-bb7a516c3c5e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398780(v=OCS.15)
ms:contentKeyID: 48184870
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Enable-CsPublicProvider

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-07_

Enables a public provider configured for use in your organization. A public provider is an organization that provides instant messaging, presence, and related services to the general public. Lync Server ships with three public providers configured but not enabled: Yahoo\!, AIM (AOL), and Messenger (MSN). This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Enable-CsPublicProvider [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Enable-CsPublicProvider [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 enables the public provider with the Identity Messenger. This command will return an error if Messenger is already enabled.

    Enable-CsPublicProvider -Identity "Messenger"

</div>

<div>

## EXAMPLE 2

Example 2 enables all the public providers that are currently disabled. In order to carry out this task, the command first uses the **Get-CsPublicProvider** cmdlet to return a collection of all the public providers configured for use in the organization. That collection is piped to the **Where-Object** cmdlet, which selects only those providers where the Enabled property is equal to False. The filtered collection is then piped to the **Enable-CsPublicProvider** cmdlet, which enables each provider in the collection.

    Get-CsPublicProvider | Where-Object {$_.Enabled -eq $False} | Enable-CsPublicProvider

</div>

<div>

## EXAMPLE 3

Example 3 enables all the public providers that are not currently enabled, provided the verification level of those providers is set to AlwaysVerifiable. To do this, the command first calls the **Get-CsPublicProvider** cmdlet to return a collection of all the public providers currently in use in the organization. This collection is piped to the **Where-Object** cmdlet, which picks out those providers that meet two criteria: 1) the VerificationLevel property is equal to AlwaysVerifiable; and, 2) the Enabled property is equal to False. (The -and operator tells the **Where-Object** cmdlet that objects must meet all the specified criteria in order to be selected.) This filtered collection is then piped to the **Enable-CsPublicProvider** cmdlet, which enables each provider in the collection.

    Get-CsPublicProvider | Where-Object {$_.VerificationLevel -eq "AlwaysVerifiable" -and $_.Enabled -eq $False} | Enable-CsPublicProvider

</div>

</div>

<div>

## Detailed Description

Federation is a means by which two organizations can set up a trust relationship that facilitates communication between the two groups. When federation has been established, users in the two organizations can send each other instant messages, subscribe for presence notifications, and otherwise communicate with one another using SIP applications such as Lync 2013. Lync Server allows for three types of federation: 1) direct federation between your organization and another; 2) federation between your organization and a public provider; and, 3) federation between your organization and a third-party hosting provider.

A public provider is an organization which provides SIP communication services for the general public. When you establish a federation relationship with a public provider, you effectively establish federation with any user who has an account hosted by that provider. For example, if you federate with Messenger (MSN), then your users will be able to exchange instant messages and presence information with anyone who has an MSN Messenger instant messaging account.

In order to federate with a public provider you need to create and enable a new public provider. (In addition, the public provider will need to create a federation relationship with you.) Public providers can be enabled at the time they are created, or they can be enabled after-the-fact by using the **Enable-CsPublicProvider** cmdlet.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Enable-CsPublicProvider** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Enable-CsPublicProvider"}

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
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Unique identifier for the public provider to be enabled. The Identity is typically the name of the website providing the services (for example,, Yahoo!; AOL; and MSN).</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Optional</p></td>
<td><p>DisplayPublicProvider object</p></td>
<td><p>Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayPublicProvider object. The **Enable-CsPublicProvider** cmdlet accepts pipelined instances of the public provider object.

</div>

<div>

## Return Types

None. Instead, the cmdlet enables instances of the Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayPublicProvider object.

</div>

<div>

## See Also


[Disable-CsPublicProvider](disable-cspublicprovider.md)  
[Get-CsPublicProvider](get-cspublicprovider.md)  
[New-CsPublicProvider](new-cspublicprovider.md)  
[Remove-CsPublicProvider](remove-cspublicprovider.md)  
[Set-CsPublicProvider](set-cspublicprovider.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

