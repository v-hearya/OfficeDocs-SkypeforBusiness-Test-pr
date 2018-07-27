---
title: Get-CsXmppGatewayConfiguration
TOCTitle: Get-CsXmppGatewayConfiguration
ms:assetid: 4c9ee876-de89-420c-bda9-9901cef47799
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204869(v=OCS.15)
ms:contentKeyID: 48184061
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Get-CsXmppGatewayConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-21_

Returns information about the XMPP gateway configuration settings in use in the organization. The extensible Messaging and Presence Protocol (XMPP) is an open-standard communications protocol for exchanging messages using XML. XMPP gateways enable Lync Server 2013 users to exchange instant message and presence information with users belonging to IM and presence providers that employ XMPP. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Get-CsXmppGatewayConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsXmppGatewayConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

In Example 1, information is returned for the XMPP gateway settings currently in use in the organization. Because Lync Server 2013 only allows for a single, global collection of gateway settings you do not need to include the Identity parameter in order to get back information for the global settings.

    Get-CsXmppGatewayConfiguration

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The Extensible Messaging and Presence Protocol (XMPP) is a standard communications protocol (based on XML) used for sending messages across the Internet. XMPP was originally named Jabber, and is supported by a number of Internet messaging and communication applications, including Google Talk and Facebook Chat.

The XMPP gateway that enables Lync 2013 to communicate with users on an XMPP network was originally released as an add-on to Microsoft Lync Server 2010; in Lync Server 2013, this functionality is built into the software. This means that your users can communicate with XMPP users provided that you:

  - <span></span>  
    Configure the XMPP gateway settings.

  - <span></span>  
    Configure the other XMPP network (for example, Google Talk) as an allowed XMPP partner.

Note that Lync Server 2013 provides only a single, global set of XMPP configuration settings: you cannot selectively enable or disable XMPP for a given site or a given Registrar pool. In fact you cannot enable or disable XMPP at all: XMPP is always enabled. If you do not want users communicating with XMPP networks then you should remove all the allowed XMPP partners. Users can only communicate with an XMPP network if that network has been configured as an allowed partner.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell command-line interface prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsXmppGatewayConfiguration"}

**Lync Server Control Panel:** The functions carried out by the **Get-CsXmppGatewayConfiguration** cmdlet are not available in the Lync Server Control Panel.

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
<td><p>Enables you to use wildcard values when referencing a collection of XMPP gateway configuration settings. Because you can only have a single, global instance of these settings there is no reason to use the Filter parameter. However, if you prefer you can use the following syntax to reference the global settings:</p>
<p>-Filter &quot;g*&quot;</p>
<p>That syntax brings back all the XMPP gateway configuration settings that have an Identity that begins with the letter &quot;g&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Unique identifier for the XMPP gateway configuration settings. Because you can only have a single, global instance of these settings, you do not need to specify an Identity when calling the <strong>Get-CsXmppGatewayConfiguration</strong> cmdlet. If you prefer, however, you can use the following syntax to reference the global settings:</p>
<p>-Identity global</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retrieves the XMPP gateway data from the local replica of the Central Management store rather than from the Central Management store itself.</p></td>
</tr>
</tbody>
</table>


</div>

<span id="InputTypes"></span>

<div>

## Input Types

None. The **Get-CsXmppGatewayConfiguration** cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **Get-CsXmppGatewayConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.XmppFederation.XmppGatewaySettings object.

</div>

<div>

## See Also


[Set-CsXmppGatewayConfiguration](set-csxmppgatewayconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

