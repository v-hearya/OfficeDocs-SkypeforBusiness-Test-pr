---
title: Managing communications in Skype for Business Online with outside users and organizations
TOCTitle: Managing communications with outside users and organizations
ms:assetid: 8a64f0fe-1e79-47d8-835e-548d7ac0757e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362813(v=OCS.15)
ms:contentKeyID: 56558833
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Managing communications in Skype for Business Online with outside users and organizations

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2015-03-09_

The following cmdlets can be used to manage federation with external domains and with public instant messaging (IM) providers:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Cmdlet</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="new-csedgeallowallknowndomains.md">New-CsEdgeAllowAllKnownDomains</a></p></td>
<td><p>Allows users to communicate with all domains except for those specified on the blocked domains list.</p>
<p>Federation is a service that enables users to exchange IM and presence information with users from other domains. Typically, administrators use allowed and blocked lists to specify the outside domains that users can communicate with.</p></td>
</tr>
<tr class="even">
<td><p><a href="new-csedgeallowlist.md">New-CsEdgeAllowList</a></p></td>
<td><p>Limits user communication to a specified collection of domains.</p>
<p>Users will be allowed to communicate only with domains that appear on the allowed domains list.</p></td>
</tr>
<tr class="odd">
<td><p><a href="new-csedgedomainpattern.md">New-CsEdgeDomainPattern</a></p></td>
<td><p>Modifies the allowed or blocked domain lists.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-cstenantfederationconfiguration.md">Get-CsTenantFederationConfiguration</a><br />
<a href="set-cstenantfederationconfiguration.md">Set-CsTenantFederationConfiguration</a></p></td>
<td><p>Enables and disables federation with other domains and federation with public providers.</p></td>
</tr>
<tr class="odd">
<td><p><a href="get-cstenanthybridconfiguration.md">Get-CsTenantHybridConfiguration</a><br />
<a href="set-cstenanthybridconfiguration.md">Set-CsTenantHybridConfiguration</a></p></td>
<td><p>Assigns the appropriate values to hybrid configuration settings.</p>
<p>In a hybrid or &quot;split domain&quot; deployment, an organization has some users with accounts homed on Skype for Business Online while simultaneously having other users with accounts homed on Lync Server 2013. By default, users homed on Skype for Business Online do not have access to the complete range of capabilities offered by Enterprise Voice. To provide Skype for Business Online users with access to these Enterprise Voice capabilities, administrators need to assign the appropriate values to hybrid configuration settings. These values can be managed only by using the <strong>CsTenantHybridConfiguration</strong> cmdlets.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-cstenantpublicprovider.md">Get-CsTenantPublicProvider</a><br />
<a href="set-cstenantpublicprovider.md">Set-CsTenantPublicProvider</a></p></td>
<td><p>Manages federation with public providers.</p>
<p>Public providers are organizations that provide SIP communication services for the general public. When you establish a federation relationship with a public provider, you effectively establish federation with any user who has an account hosted by that provider.</p></td>
</tr>
</tbody>
</table>


You can also manage federation settings, for both federated domains and for public providers, by using the Skype for Business Online admin center:

![Lync Online admin center organization settings](images/Dn362813.f860d03f-5906-49b0-bcc7-7634afe7005e(OCS.15).png "Lync Online admin center organization settings")

<div>

## See Also


[The Skype for Business Online cmdlets](the-skype-for-business-online-cmdlets.md)  
[Quick reference: Using Windows PowerShell to do common Skype for Business Online management tasks](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

