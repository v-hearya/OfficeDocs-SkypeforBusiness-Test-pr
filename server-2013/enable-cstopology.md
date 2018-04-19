---
title: Enable-CsTopology
TOCTitle: Enable-CsTopology
ms:assetid: 5aedffa0-9ca1-4aec-b4ad-c3e409c0ffb2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398398(v=OCS.15)
ms:contentKeyID: 48184230
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Enable-CsTopology

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-04_

Enables the most recently published Lync Server topology. After you have made changes to your topology, the changes will not take effect until they have been both published and enabled. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Enable-CsTopology [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-Report <String>] [-SkipPrepareCheck <$true | $false>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

The command shown in Example 1 enables the most recently published topology.

    Enable-CsTopology

</div>

</div>

<div>

## Detailed Description

After you have installed Lync Server you will eventually need to make changes to the infrastructure; for example, you might need to add a new site, delete an existing Registrar pool, or add an additional Archiving Server. These infrastructure changes must be made by using Topology Builder. After you have made the changes in Topology Builder, you can then publish and enable those changes using that same tool. These latter two steps are very important: although you can make as many modifications as you want using Topology Builder, those modifications do not actually take effect, and your infrastructure will not actually change, until the modifications have been published and the new topology has been enabled.

When changes are published, the new information (for example, a new site or a new server role) is written to the Central Management store. However, these new (or newly modified) objects do not immediately join your topology; that occurs only when the updated topology has been enabled. If you select the Publish option in Topology Builder you can carry out both of these steps at the same time: the changes will be published (written to the Central Management store) and the new topology will be enabled.

There might be times, however, when you would prefer to publish your changes and enable your topology as separate steps; doing so gives you an opportunity to confirm that deployment has succeeded before you bring the new objects into the topology. To separately publish and then enable topology changes, you must do the following:

Publish the modified topology in Topology Builder. (Due to late changes in the product, we recommend that publishing always take place using Topology Builder.)

Use the **Enable-CsTopology** cmdlet to cause the published changes to take effect.

From time-to-time you might also need to call the **Enable-CsTopology** cmdlet in order to enable changes made outside Topology Builder. For example, the cmdlet must be run after you have used the CsKerberosAccountAssignment cmdlets to modify Kerberos web authentication.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Enable-CsTopology** cmdlet locally: RTCUniversalServerAdmins. However, if setup permissions have not been delegated, then you must be a domain administrator in order to run the cmdlet. In order to give RTCUniversalServerAdmins the right to actually use the **Enable-CsTopology** cmdlet, you must run the **Grant-CsSetupPermission** cmdlet against every Active Directory container that contains computers running Lync Server services. Note that this restriction also applies to enabling a topology through Topology Builder. If you have not delegated permissions by using the **Grant-CsSetupPermission** cmdlet, then only a domain administrator will be able to enable a topology through Topology Builder.

In addition, you must be a local administrator on any computer where Lync Server file shares are to be created; this is required in order to set the necessary security permissions on the shared folders. Alternatively, you can run the **Enable-CsTopology** cmdlet if you have full control over the file share. That enables the cmdlet to create the shared folders and set share-level security permissions. However, a local administrator will then need to add the share-level security permissions.

To verify that setup permissions have been delegated, run the **Test-CsSetupPermission** cmdlet against any Active Directory containers containing computers running Lync Server services.

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
<td><p><em>GlobalCatalog</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Fully qualified domain name (FQDN) of a global catalog server in your domain. This parameter is not required if you are running the <strong>Enable-CsTopology</strong> cmdlet on a computer with an account in your domain.</p></td>
</tr>
<tr class="even">
<td><p><em>GlobalSettingsDomainController</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>FQDN of a domain controller where global settings are stored. If global settings are stored in the System container in Active Directory Domain Services, then this parameter must point to the root domain controller. If global settings are stored in the Configuration container, then any domain controller can be used and this parameter can be omitted.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Enables you to specify a file path for the log file created when the cmdlet runs. For example: -Report &quot;C:\Logs\Enable_Topology.html&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>SkipPrepareCheck</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>If set to True ($True) the <strong>Enable-CsTopology</strong> cmdlet will skip its initial preparation check.</p></td>
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

None. The **Enable-CsTopology** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

None. Instead, the **Enable-CsTopology** cmdlet enables instances of the Microsoft.Rtc.Management.Deploy.Internal.DefaultTopology object.

</div>

<div>

## See Also


[Get-CsTopology](get-cstopology.md)  
[Grant-CsSetupPermission](grant-cssetuppermission.md)  
[Publish-CsTopology](publish-cstopology.md)  
[Test-CsSetupPermission](test-cssetuppermission.md)  
[Test-CsTopology](test-cstopology.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

