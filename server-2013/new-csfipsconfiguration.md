---
title: New-CsFIPSConfiguration
TOCTitle: New-CsFIPSConfiguration
ms:assetid: 9ce030fb-fb6b-47a2-9fb9-69e8369b43be
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205114(v=OCS.15)
ms:contentKeyID: 48184910
ms.date: 10/29/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# New-CsFIPSConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-10-29_

Creates a new collection of Federal Information Processing Standards (FIPS) configuration settings. The FIPS standards are a set of United States government security standards required for use in computers maintained by non-military government agencies and by government contractors. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    New-CsFIPSConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-RequireFIPSCompliantMedia <$true | $false>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The commands shown in Example 1 create a new, in-memory-only set of FIPS configuration settings and then later use these settings to update the global collection of FIPS configuration settings. In order to do this, the first command in the example uses the **New-CsFIPSConfiguration** cmdlet and the InMemory parameter to create a new collection of FIPS configurations settings with the Identity "global"; the resulting settings object is stored in a variable named $x.

In the second command, the **Set-CsFIPSConfiguration** cmdlet and the Instance parameter are then used to replace the existing global collection of FIPS settings with the new collection stored in $x.

Although this example works, it is easier to modify FIPS configuration settings by using the **Set-CsFIPSConfiguration** cmdlet.

    $x = New-CsFIPSConfiguration -Identity "global" -RequireFIPSCompliantMedia $False -InMemory
    
    Set-CsFIPSConfiguration -Instance $x

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The Federal Information Processing Standards (FIPS) are a series of standards and guidelines used by computers engaged in work for the United States government; for example, there are FIPS standards that govern the use of such things as cryptography, encryption, and digital signatures. (See <http://www.itl.nist.gov/fipspubs/by-num.htm> for more information.) Lync Server 2013 provides an option that enables the software to use only algorithms that meet the FIPS standards. If you need to work with the United States government (or with other entities that follow FIPS) then you can enable FIPS compliance in Lync Server 2013.

Keep in mind, however, that, for the on-premises version of Lync Server, you have only a single, global collection of FIPS configuration settings: FIPS compliance can only be enabled or disabled for your entire Lync Server implementation. You cannot selectively enable or disable FIPS compliance on, say, an individual site or an individual Registrar pool. If you do enable FIPS compliance, you could potentially encounter problems when trying to communicate with organizations that do not fully adhere to the FIPS standards. That means that the **New-CsFIPSConfiguration** cmdlet is primarily used to manage FIPS compliance for Lync Online.

By default, FIPS compliance is disabled in Lync Server 2013.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsFIPSConfiguration"}

**Lync Server Control Panel:** The functions carried out by the New-CsFIPSConfiguration cmdlet are not available in the Lync Server Control Panel.

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
<td><p>Required</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Unique identifier for the new collection of FIPS configuration settings. Because Lync Server 2013 only supports a single, global collection of FIPS settings, the only way you can use this parameter is to create a &quot;new&quot; global collection that exists only in memory. You will also need to use the InMemory parameter in order to do that.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="even">
<td><p><em>InMemory</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet’s matching Set- cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><em>RequireFIPSCompliantMedia</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>When set to True, Lync Server 2013 will only allow media sessions with entities that use FIPS compliant algorithms for authentication and authorization.</p>
<p>Note that, if you require FIPS compliance, then your users will no longer be able to connect to your system by using a Microsoft Lync Server 2010 A/V Edge server. Instead, you will need to upgrade all your Edge servers to Lync 2013. Additionally, users with Lync 2010 (or earlier) clients will no longer be able to access media via a 2013 A/V Edge server.</p>
<p>The default value is False.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Guid</p></td>
<td><p>Globally unique identifier (GUID) of the Lync Online tenant account for which the new FIPS configuration settings are being created. For example:</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>You can return the tenant ID for each of your tenants by running this command:</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
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

None. The **New-CsFIPSConfiguration** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **New-CsFIPSConfiguration** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.FIPSConfiguration.FIPSConfiguration object.

</div>

<div>

## See Also


[Get-CsFIPSConfiguration](get-csfipsconfiguration.md)  
[Remove-CsFIPSConfiguration](remove-csfipsconfiguration.md)  
[Set-CsFIPSConfiguration](set-csfipsconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

