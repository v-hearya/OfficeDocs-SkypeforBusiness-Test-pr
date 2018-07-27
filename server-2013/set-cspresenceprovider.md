---
title: Set-CsPresenceProvider
TOCTitle: Set-CsPresenceProvider
ms:assetid: 3f2e30d1-edb5-4839-a24f-11b77b699a1d
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204833(v=OCS.15)
ms:contentKeyID: 48183944
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsPresenceProvider

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-07_

Modifies a presence provider configured for use in the organization. Presence providers represent the PresenceProviders property of a collection of user services configuration settings. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Set-CsPresenceProvider [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsPresenceProvider [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The commands shown in Example 1 demonstrate how you can use the **Set-CsPresenceProvider** cmdlet to modify the FQDN of an existing presence provider. To do this, the first command in the example uses the **Get-CsPresenceProvider** cmdlet to create an object reference to the presence provider with the Identity "global/contoso.com". This object reference is stored in the variable $x.

In the second command, the FQDN property of the object reference is set to contoso2.com, the new FQDN for the presence provider. After the FQDN property has been configured, the **Set-CsPresenceProvider** cmdlet is used, along with the Instance property, to write these changes to the global collection of User Services configuration settings.

    $x = Get-CsPresenceProvider -Identity "global/contoso.com" 
    $x.Fqdn = "contoso2.com"
    Set-CsPresenceProvider -Instance $x

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The **CsPresenceProvider** cmdlets are used to manage the PresenceProviders property found in the User Services configuration settings. Among other things, these settings are used to maintain presence information, including a collection of authorized presence providers. That collection is stored in the PresenceProviders property.

The **Set-CsPresenceProvider** cmdlet can be used to modify the FQDN of a presence provider currently configured for use in the organization.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsPresenceProvider"}

**Lync Server Control Panel:** The functions carried out by the **Set-CsPresenceProvider** cmdlet are not available in the Lync Server Control Panel.

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
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Unique identifier for the presence provider to be modified. The Identity of a presence provider is composed of two parts: the scope (Parent) where the rule has been applied (for example, service:UserServer:atl-cs-001.litwareinc.com) and the provider Fqdn. To modify a presence provider at the global scope use syntax similar to this:</p>
<p>-Identity &quot;global/fabrikam.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.PSObject</p></td>
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

<span id="InputTypes"></span>

<div>

## Input Types

The **Set-CsPresenceProvider** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PresenceProvider\#Decorated object.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

None. Instead, the **Set-CsPresenceProvider** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.PresenceProvider\#Decorated object.

</div>

<div>

## See Also


[Get-CsPresenceProvider](get-cspresenceprovider.md)  
[Get-CsUserServicesConfiguration](get-csuserservicesconfiguration.md)  
[New-CsPresenceProvider](new-cspresenceprovider.md)  
[Remove-CsPresenceProvider](remove-cspresenceprovider.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

