---
title: Set-CsExUmContact
TOCTitle: Set-CsExUmContact
ms:assetid: c0fe0fdc-6fea-4334-8645-24ffd494db07
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412944(v=OCS.15)
ms:contentKeyID: 48185310
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Set-CsExUmContact

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-25_

Modifies an existing Auto Attendant or Subscriber Access contact object for hosted Exchange Unified Messaging (UM). This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Set-CsExUmContact -Identity <UserIdParameter> [-AutoAttendant <$true | $false>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-DisplayNumber <String>] [-DomainController <Fqdn>] [-Enabled <$true | $false>] [-EnterpriseVoiceEnabled <$true | $false>] [-ExchangeArchivingPolicy <Uninitialized | UseLyncArchivingPolicy | NoArchiving | ArchivingToExchange>] [-PassThru <SwitchParameter>] [-SipAddress <String>] [-WhatIf [<SwitchParameter>]]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example sets the AutoAttendant property of the Exchange UM contact with the SIP address exumsa4@fabrikam.com to True. We first call the **Get-CsExUmContact** cmdlet to retrieve the contact object. (We could also have used the contact’s Active Directory display name, the contact’s user principal name, or the contact’s logon name.) This command retrieves the one contact with the provided Identity. That contact is then passed to the **Set-CsExUmContact** cmdlet, where we set its AutoAttendant parameter to True.

    Get-CsExUmContact -Identity sip:exumsa4@fabrikam.com | Set-CsExUmContact -AutoAttendant $True

</div>

<div>

## EXAMPLE 2

This example is identical to Example 1, but instead of retrieving the contact by calling the **Get-CsExUmContact** cmdlet and piping that object to the **Set-CsExUmContact** cmdlet, we provide the **Set-CsExUmContact** cmdlet with the Identity of the contact we want to modify. Notice the format of the Identity: in this case we’ve used the full distinguished name of the contact object, which includes an auto-generated GUID (generated at the time the contact was created). We then set the AutoAttendant parameter of the contact to True.

    Set-CsExUmContact -Identity "CN={1bf6208d-2847-45d0-828f-636f14da858b},OU=ExUmContacts,DC=litwareinc,DC=com" -AutoAttendant $True

</div>

</div>

<div>

## Detailed Description

Lync Server works with Exchange UM to provide several voice-related capabilities, including Auto Attendant and Subscriber Access. When Exchange UM is provided as a hosted service (rather than on premises), contact objects must be created by using Windows PowerShell to apply the Auto Attendant and Subscriber Access functionality. These objects are created by calling the **New-CsExUmContact** cmdlet and can later be modified by using the **Set-CsExUmContact** cmdlet.

The easiest way to use this cmdlet is often to first call the **Get-CsExUmContact** cmdlet to retrieve an instance of the contact object you want to modify. Simply pipe the output of the **Get-CsExUmContact** cmdlet command to the **Set-CsExUmContact** cmdlet and assign values to the parameters for the properties you want to change. (For details, see the Examples section in this topic.) Alternatively, you can call the **Set-CsExUmContact** cmdlet, passing it the Identity of the contact object you want to modify.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Set-CsExUmContact** cmdlet locally: RTCUniversalUserAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsExUmContact"}

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
<td><p>The unique identifier of the contact object you want to modify. Contact identities can be specified using one of four formats: 1) The contact’s SIP address; 2) the contact's user principal name (UPN); 3) the contact's domain name and logon name, in the form domain\logon (for example, litwareinc\exum1); and, 4) the contact's Active Directory display name (for example, Team Auto Attendant).</p>
<p>Full data type: Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
</tr>
<tr class="even">
<td><p><em>AutoAttendant</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>Set the parameter to True if the contact object is an Auto Attendant. This parameter is False by default.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Prompts you for confirmation before executing the command.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>A description of this contact. The description is for use by administrators to identify the type of contact (Auto Attendant or Subscriber Access), the location, provider, or any other information that will identify the purpose of each Exchange UM contact.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisplayNumber</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The telephone number of the contact. Display numbers for each contact must be unique (no two Exchange UM contacts can have the same display number). Changing this value will also change the value of the LineURI property.</p>
<p>This value may begin with a plus sign (+) and may contain any number of digits. The first digit cannot be zero.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>Optional</p></td>
<td><p>Fqdn</p></td>
<td><p>Allows you to specify a domain controller. If no domain controller is specified, the first available will be used.</p></td>
</tr>
<tr class="odd">
<td><p><em>Enabled</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>Indicates whether or not the contact has been enabled for Lync Server. Setting this parameter to False will disable the contact, and the Auto Attendant or Subscriber Access associated with this contact will no longer function.</p>
<p>If you disable an account by using the Enabled parameter, the information associated with that account (including assigned hosted voice mail policies) is retained. If you later re-enable the account using the Enable parameter, the associated account information will be restored.</p></td>
</tr>
<tr class="even">
<td><p><em>EnterpriseVoiceEnabled</em></p></td>
<td><p>Optional</p></td>
<td><p>Boolean</p></td>
<td><p>Indicates whether the contact has been enabled for Enterprise Voice. If this value is set to False, the Auto Attendant or Subscriber Access feature associated with this contact will no longer be available.</p></td>
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
<td><p><em>PassThru</em></p></td>
<td><p>Optional</p></td>
<td><p>witchParameter</p></td>
<td><p>Returns the results of the command. By default, this cmdlet does not generate any output.</p></td>
</tr>
<tr class="odd">
<td><p><em>SipAddress</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The SIP address of the contact. This must be a new address that does not already exist as a user or contact in Active Directory Domain Services.</p>
<p>Changing this value will also change the SIP address stored in the OtherIpPhone property.</p>
<p>The SipAddress can be used as the Identity value for the <strong>Get-CsExUmContact</strong> cmdlet commands to retrieve specific contacts. When calling that cmdlet, the new SipAddress will be used; queries for the old SIP address will not return an object.</p></td>
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

Microsoft.Rtc.Management.ADConnect.Schema.OCSADExUmContact object. Accepts pipelined input of Exchange UM contact objects.

</div>

<div>

## Return Types

This cmdlet modifies an object of type Microsoft.Rtc.Management.ADConnect.Schema.OCSADExUmContact. When the PassThru parameter is used, it also returns an object of this type.

</div>

<div>

## See Also


[New-CsExUmContact](new-csexumcontact.md)  
[Remove-CsExUmContact](remove-csexumcontact.md)  
[Get-CsExUmContact](get-csexumcontact.md)  
[Move-CsExUmContact](move-csexumcontact.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

