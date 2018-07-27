---
title: Get-CsVoicemailReroutingConfiguration
TOCTitle: Get-CsVoicemailReroutingConfiguration
ms:assetid: 25e401eb-6a84-468f-b0eb-5b794f20b5bc
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425732(v=OCS.15)
ms:contentKeyID: 48183656
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsVoicemailReroutingConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-06_

Retrieves settings that provide public switched telephone network (PSTN) phone numbers to access Exchange UM Subscriber Access and Auto Attendant features. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Get-CsVoicemailReroutingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsVoicemailReroutingConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example retrieves all of the voice mail rerouting configuration settings defined in this deployment of Lync Server. For example, if there are three branch offices where a Survivable Branch Appliance is deployed, this command will return three voice mail rerouting configuration sets.

    Get-CsVoicemailReroutingConfiguration

</div>

<div>

## EXAMPLE 2

This example retrieves the voice mail rerouting configuration settings for the site BranchOffice\_Portland.

    Get-CsVoicemailReroutingConfiguration -Identity site:BranchOffice_Portland

</div>

<div>

## EXAMPLE 3

This example retrieves all the voice mail rerouting settings for all sites with site names beginning with the string BranchOffice (for example, BranchOffice\_Portland, BranchOffice\_Sacramento).

    Get-CsVoicemailReroutingConfiguration -Filter *:BranchOffice*

</div>

<div>

## EXAMPLE 4

This example retrieves all the voice mail rerouting configurations that are not enabled. The first part of this command is a call to the **Get-CsVoicemailReroutingConfiguration** cmdlet, which retrieves a collection of all the voice mail rerouting configurations. That collection is then piped to the **Where-Object** cmdlet. The **Where-Object** cmdlet narrows that collection down to include only the configurations that have an Enabled property equal to (-eq) False.

    Get-CsVoicemailReroutingConfiguration | Where-Object {$_.Enabled -eq $False}

</div>

</div>

<div>

## Detailed Description

This cmdlet retrieves settings that determine where Auto Attendant and Subscriber Access calls are rerouted to when IP connectivity from Lync Server in the branch site to the Exchange UM Server located in the data center is not available.

Auto Attendant and Subscriber Access are features of Exchange UM. The Auto Attendant feature provides voice recognition and touch-tone control (dual-tone multifrequency, or DTMF) so that outside callers can navigate a company’s phone system to reach the department or employee they want or, in Message Taking Mode, to accept messages for users. (Voice rerouting for Message Taking Mode is recommended.) Subscriber Access allows internal users to access their Microsoft Outlook mailbox from a phone. The numbers provided by these settings allow callers to leave voice mail messages for Enterprise Voice users (the AutoAttendantNumber setting) and for those users to retrieve voice mail even if the IP connectivity from the Lync Server deployment at a remote site to Exchange UM in the data center is unavailable (the SubscriberAccessNumber setting).

Calling this cmdlet with no parameters will return all voice mail rerouting configurations.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Get-CsVoicemailReroutingConfiguration** cmdlet locally: RTCUniversalUserAdmins, RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsVoicemailReroutingConfiguration"}

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
<td><p>The Filter parameter allows you to retrieve configuration settings for a particular set of sites based on wildcard matching.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>The unique identifier of the configuration you want to retrieve. For this cmdlet the Identity will be either Global or Site:&lt;site name&gt;, where &lt;site name&gt; is the name of the site to which the settings are applied.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the voice mail rerouting configuration from the local replica of the Central Management store, rather than the Central Management store itself.</p></td>
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

Retrieves one or more objects of type Microsoft.Rtc.Management.WritableConfig.Settings.ExumRouting.VoicemailReroutingConfiguration.

</div>

<div>

## See Also


[New-CsVoicemailReroutingConfiguration](new-csvoicemailreroutingconfiguration.md)  
[Remove-CsVoicemailReroutingConfiguration](remove-csvoicemailreroutingconfiguration.md)  
[Set-CsVoicemailReroutingConfiguration](set-csvoicemailreroutingconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

