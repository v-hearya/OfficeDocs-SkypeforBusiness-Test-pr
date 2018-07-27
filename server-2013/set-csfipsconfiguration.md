---
title: Set-CsFIPSConfiguration
TOCTitle: Set-CsFIPSConfiguration
ms:assetid: 920f58ce-e175-41ac-b681-5ac873091593
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205084(v=OCS.15)
ms:contentKeyID: 48184796
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsFIPSConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Modifies an existing collection of Federal Information Processing Standards (FIPS) configuration settings. The FIPS standards are a set of United States government security standards required for use in computers maintained by non-military government agencies and by government contractors. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Set-CsFIPSConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsFIPSConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-RequireFIPSCompliantMedia <$true | $false>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

In Example 1, the RequireFIPSCompliantMedia property of the global FIPS configuration settings is set to True ($True).

    Set-CsFIPSConfiguration -Identity "global" -RequireFIPSCompliantMedia $True

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The Federal Information Processing Standards (FIPS) are a series of standards and guidelines used by computers engaged in work for the United States government; for example, there are FIPS standards that govern the use of such things as cryptography, encryption, and digital signatures. (See <http://www.itl.nist.gov/fipspubs/by-num.htm> for more information.) Lync Server 2013 provides an option that enables the software to use only algorithms that meet the FIPS standards. If you need to work with the United States government (or with other entities that follow FIPS) then you can enable FIPS compliance in Lync Server 2013.

Keep in mind, however, that, for the on-premises version of Lync Server, you have only a single, global collection of FIPS configuration settings: FIPS compliance can only be enabled or disabled for your entire Lync Server implementation. You cannot selectively enable or disable FIPS compliance on, say, an individual site or an individual Registrar pool. If you do enable FIPS compliance, you could potentially encounter problems when trying to communicate with organizations that do not fully adhere to the FIPS standards.

By default, FIPS compliance is disabled in Lync Server 2013.

The **Set-CsFIPSConfiguration** cmdlet is used to enable or disable FIPS compliance.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsFIPSConfiguration"}

**Lync Server Control Panel:** The functions carried out by the **Set-CsFIPSConfiguration** cmdlet are not available in the Lync Server Control Panel.

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
<td><p>Unique Identity of the FIPS configuration settings to be modified. Because Lync Server 2013 only supports a single, global collection of FIPS settings, the only collection that can be modified is the global collection:</p>
<p>-Identity global</p>
<p>If you do not include this parameter the <strong>Set-CsFIPSConfiguration</strong> cmdlet will modify the global collection.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.PSObject</p></td>
<td><p>Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.</p></td>
</tr>
<tr class="odd">
<td><p><em>RequireFIPSCompliantMedia</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>When set to True Lync Server 2013 will only allow media sessions with entities that use FIPS compliant algorithms for authentication and authorization.</p>
<p>Note that, if you require FIPS compliance, then your users will no longer be able to connect to your system by using a Microsoft Lync Server 2010 A/V Edge server. Instead, you will need to upgrade all your Edge servers to Lync 2013.</p>
<p>The default value is False.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Guid</p></td>
<td><p>Globally unique identifier (GUID) of the Lync Online tenant account for which the FIPS configuration settings are being modified. For example:</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>You can return the tenant ID for each of your tenants by running this command:</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>executed the command without actually executing the command.</p></td>
</tr>
</tbody>
</table>


</div>

<span id="InputTypes"></span>

<div>

## Input Types

The **Set-CsFIPSConfiguration** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.FIPSConfiguration.FIPSConfiguration object.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

None. Instead, the **Set-CsFIPSConfiguration** cmdlet modifies existing instances of the Microsoft.Rtc.Management.WritableConfig.Settings.FIPSConfiguration.FIPSConfiguration object.

</div>

<div>

## See Also


[Get-CsFIPSConfiguration](get-csfipsconfiguration.md)  
[New-CsFIPSConfiguration](new-csfipsconfiguration.md)  
[Remove-CsFIPSConfiguration](remove-csfipsconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

