---
title: Set-CsAnalogDevice
TOCTitle: Set-CsAnalogDevice
ms:assetid: b05e729e-cdef-4c78-8ce7-b183c3208a93
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412843(v=OCS.15)
ms:contentKeyID: 48185106
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsAnalogDevice

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-25_

Modifies an existing device in the collection of analog devices that can be managed by using Lync Server. An analog device is a telephone or other device that is connected to the public switched telephone network (PSTN). This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsAnalogDevice -Identity <UserIdParameter> [-AnalogFax <$true | $false>] [-Confirm [<SwitchParameter>]] [-DisplayName <String>] [-DisplayNumber <String>] [-DomainController <Fqdn>] [-Enabled <$true | $false>] [-EnterpriseVoiceEnabled <$true | $false>] [-ExchangeArchivingPolicy <Uninitialized | UseLyncArchivingPolicy | NoArchiving | ArchivingToExchange>] [-Gateway <Fqdn>] [-LineURI <String>] [-PassThru <SwitchParameter>] [-SipAddress <String>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 changes the value of the LineUri property for the analog device that has the Identity CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com.

    Set-CsAnalogDevice -Identity "CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com" -LineUri "TEL:+14255551298"

</div>

<div>

## EXAMPLE 2

The command shown in Example 2 changes the gateway for each analog device currently using the gateway 192.168.0.240. To perform this task, the **Get-CsAnalogDevice** cmdlet is called along with the Filter parameter; the filter value {Gateway -eq "192.168.0.240"} ensures that only devices with a Gateway equal to (-eq) 192.168.0.240 are returned. This filtered collection is then piped to the **Set-CsAnalogDevice** cmdlet, which takes each item in the collection and changes the value of the Gateway property to 192.168.1.100.

    Get-CsAnalogDevice -Filter {Gateway -eq "192.168.0.240"} | Set-CsAnalogDevice -Gateway "192.168.1.100"

</div>

</div>

<div>

## Detailed Description

Analog devices include telephones, fax machines, modems, and teletype/telecommunication device for the deaf (TTY/TDD) devices that are connected to the public switched telephone network (PSTN). Unlike devices that take advantage of Enterprise Voice (that is, the Voice over Internet Protocol (VoIP) solution offered by Microsoft), analog devices do not transmit information by using digital packets. Instead, information is transmitted by using a continuous signal. This signal is commonly referred to as an analog signal; hence the term "analog devices."

In order to enable administrators to manage analog devices, Lync Server lets you associate analog devices with Active Directory contact objects. After a device has been associated with a contact object, you can then manage the analog device by assigning policies and dial plans to the contact.

The **Set-CsAnalogDevice** cmdlet provides a way for you to modify the properties of the contact objects associated with analog devices. For example, you can change the contact’s Active Directory display name or the line Uniform Resource Identifier (URI) associated with the device.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsAnalogDevice** cmdlet locally: RTCUniversalUserAdmins. Permissions to run this cmdlet for specific sites or specific Active Directory organizational (OUs) can be assigned by using the **Grant-CsOUPermission** cmdlet. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsAnalogDevice"}

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
<td><p>UserIdParameter</p></td>
<td><p>Unique identifier for the analog device being modified. Analog devices are identified by using the Active Directory distinguished name (DN) of the associated contact object. By default, analog devices use a GUID (globally unique identifier) as their common name, which means devices will typically have an Identity similar to this: CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com. This means you might find it easier to modify analog devices by using the <strong>Get-CsAnalogDevice</strong> cmdlet to return the analog devices objects and then piping those objects to the <strong>Set-CsAnalogDevice</strong> cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>AnalogFax</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>Set to True ($True) if the analog device is a fax machine. Set to False ($False) if the device is not a fax machine.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>DisplayName</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>Configures the Active Directory display name of the analog device.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisplayNumber</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>Phone number as displayed in Lync. The DisplayNumber property can be formatted any way you prefer; for example 1-800-555-1234; 1-(800)-555-1234; 1.800.555.1234; etc.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>Optional</p></td>
<td><p>Fqdn</p></td>
<td><p>Enables you to connect to the specified domain controller in order to modify contact information. To connect to a particular domain controller, include the DomainController parameter followed by the computer name (for example, atl-mcs-001) or its fully qualified domain name (FQDN) (for example, atl-mcs-001.litwareinc.com).</p></td>
</tr>
<tr class="odd">
<td><p><em>Enabled</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>When set to True ($True) the analog device can be used with Lync.</p></td>
</tr>
<tr class="even">
<td><p><em>EnterpriseVoiceEnabled</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>Indicates whether the contact object for the analog device has been enabled for Enterprise Voice, the VoIP solution offered by Microsoft. With Enterprise Voice, telephone calls can be made using the Internet rather than using the standard telephone network.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExchangeArchivingPolicy</em></p></td>
<td><p>Optional</p></td>
<td><p>ExchangeArchivingPolicyOptionsEnum</p></td>
<td><p>Indicates where the contact's instant messaging sessions are archived. Allowed values are:</p>
<p>* Uninitialized</p>
<p>* UseLyncArchivingPolicy</p>
<p>* ArchivingToExchange</p>
<p>* NoArchiving</p></td>
</tr>
<tr class="even">
<td><p><em>Gateway</em></p></td>
<td><p>Optional</p></td>
<td><p>Fqdn</p></td>
<td><p>IP address of the PSTN gateway to be used by the analog device.</p></td>
</tr>
<tr class="odd">
<td><p><em>LineURI</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>Phone number for the analog device. The line URI should be specified by using the E.164 format, and be prefixed by the &quot;TEL:&quot; prefix. For example: TEL:+14255551297. Any extension number should be added to the end of the line URI; for example: TEL:+14255551297;ext=51297.</p></td>
</tr>
<tr class="even">
<td><p><em>PassThru</em></p></td>
<td><p>Optional</p></td>
<td><p>witchParameter</p></td>
<td><p>Returns an object representing the common area phone.</p></td>
</tr>
<tr class="odd">
<td><p><em>SipAddress</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>Unique identifier that allows the analog device to communicate with SIP devices such as Lync 2013. The SIP address must be prefaced by the prefix &quot;sip:&quot;. For example: sip:bldg14lobby@litwareinc.com.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Describes what would happen if you executed the command without actually executing the command.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

Microsoft.Rtc.Management.ADConnect.Schema.OCSADAnalogDeviceContact object. The **Set-CsAnalogDevice** cmdlet accepts pipelined instances of the analog device object.

</div>

<div>

## Return Types

By default, the **Set-CsAnalogDevice** cmdlet does not return any objects or values. However, if you include the PassThru parameter, the cmdlet will return instances of the Microsoft.Rtc.Management.ADConnect.Schema.OCSADAnalogDeviceContact object.

</div>

<div>

## See Also


[Get-CsAnalogDevice](get-csanalogdevice.md)  
[Move-CsAnalogDevice](move-csanalogdevice.md)  
[New-CsAnalogDevice](new-csanalogdevice.md)  
[Remove-CsAnalogDevice](remove-csanalogdevice.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

