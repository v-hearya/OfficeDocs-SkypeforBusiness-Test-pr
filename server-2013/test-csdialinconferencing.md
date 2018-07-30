---
title: Test-CsDialInConferencing
TOCTitle: Test-CsDialInConferencing
ms:assetid: e4aedf4f-77ac-4c8b-9613-07f8ea12c041
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg399013(v=OCS.15)
ms:contentKeyID: 48185730
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Test-CsDialInConferencing

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-28_

The **Test-CsDialInConferencing** cmdlet checks to see if a user can take part in a dial-in conferencing session. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Test-CsDialInConferencing -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetPstnPhoneNumber <String>] [-UserSipAddress <String>] [-VerifyConferenceJoin <$true | $false>] <COMMON PARAMETERS>

    Test-CsDialInConferencing -UserCredential <PSCredential> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] [-TargetPstnPhoneNumber <String>] [-VerifyConferenceJoin <$true | $false>] <COMMON PARAMETERS>

    Test-CsDialInConferencing [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 verifies that a preconfigured test user can take part in dial-in conferencing on the pool atl-cs-001.litwareinc.com. This command will work only if test users have been defined for the pool atl-cs-001.litwareinc.com. If they have, then the command will determine whether or not the first test user is able to log on to Lync Server.

If test users have not been defined, then the command will fail because it will not know which user to log on as. If you have not defined test users for a pool, then you must include the UserCredential parameter and the credentials of the user that the command should employ when trying to log on.

    Test-CsDialInConferencing -TargetFqdn atl-cs-001.litwareinc.com 

</div>

<div>

## EXAMPLE 2

The commands shown in Example 2 test the ability of a specific user (litwareinc\\pilar) to take part in dial-in conferencing on the pool atl-cs-001.litwareinc.com. To do this, the first command in the example uses the **Get-Credential** cmdlet to create a Windows PowerShell credential object containing the name and password of the user Pilar Ackerman. (Because the logon name –litwareinc\\pilar -- has been included as a parameter, the administrator only has to enter the password for the Pilar Ackerman account in the Windows PowerShell Credential Request dialog box.) The resulting credentials object is then stored in a variable named $cred1.

The second command then checks to see if the user Pilar Ackerman can log on to the pool atl-cs-001.litwareinc.com and take part in a dial-in conference. To carry out this task, the **Test-CsDialInConferencing** cmdlet is called, along with three parameters: TargetFqdn (the FQDN of the Registrar pool); UserCredential (the Windows PowerShell object containing Pilar Ackerman’s user credentials); and UserSipAddress (the SIP address corresponding to the supplied user credentials).

    $cred1 = Get-Credential "litwareinc\pilar"
    
    Test-CsDialInConferencing -TargetFqdn atl-cs-001.litwareinc.com -UserSipAddress "sip:pilar@litwareinc.com" -UserCredential $cred1

</div>

</div>

<div>

## Detailed Description

The **Test-CsDialInConferencing** cmdlet is an example of a Lync Server "synthetic transaction." Synthetic transactions are used in Lync Server to verify that users are able to successfully complete common tasks such as logging on to the system, exchanging instant messages, or making calls to a phone located on the public switched telephone network (PSTN). These tests can be conducted manually by an administrator, or they can be automatically run by an application such as Microsoft System Center Operations Manager (formerly Microsoft Operations Manager).

Synthetic transactions are typically conducted in two different ways. Many administrators will use the **CsHealthMonitoringConfiguration** cmdlets to set up test users for each of their Registrar pools. These test users are a pair of users who have been preconfigured for use with synthetic transactions. (Typically these are test accounts and not accounts that belong to actual users.) With test users configured for a pool, administrators can simply run a synthetic transaction against that pool without having to specify the identities of (and supply the credentials for) the user accounts involved in the test.

Alternatively, administrators can run a synthetic transaction using actual user accounts. For example, if two users are unable to exchange instant messages, an administrator could run a synthetic transaction using the two user accounts in question (as opposed to a pair of test accounts) and try to diagnose and resolve the problem. If you decide to conduct a synthetic transaction using actual user accounts, you will need to supply the logon names and passwords for each user.

The **Test-CsDialInConferencing** cmdlet works by attempting to log a test user onto the system. (If you are using test users, the **Test-CsDialInConferencing** cmdlet will use the first test account configured for that pool.) If logon succeeds, the cmdlet will then use the user’s credentials and permissions to try the available dial-in conferencing access numbers. The success or failure of each dial-in attempt will be noted, then the test user will be logged off from Lync Server.

The **Test-CsDialInConferencing** cmdlet only verifies that the appropriate connections can be made. The cmdlet does not actually make any phone calls or create any dial-in conferences that other users can join.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Test-CsDialInConferencing** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsDialInConferencing"}

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
<td><p><em>TargetFqdn</em></p></td>
<td><p>Required</p></td>
<td><p>System.String</p></td>
<td><p>Fully qualified domain name (FQDN) of the pool to be tested.</p></td>
</tr>
<tr class="even">
<td><p><em>UserCredential</em></p></td>
<td><p>Required</p></td>
<td><p>System.Management.Automation.PSCredential</p></td>
<td><p>User credential object for the user account to be tested. The value passed to UserCredential should be an object reference obtained by using the <strong>Get-Credential</strong> cmdlet. For example, this code returns a credentials object for the user litwareinc\kenmyer and stores that object in a variable named $x:</p>
<p>$x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>You need to supply the user password when running this command. This parameter is not required if you are conducting the test using the health monitoring configuration settings.</p></td>
</tr>
<tr class="odd">
<td><p><em>Authentication</em></p></td>
<td><p>Optional</p></td>
<td><p>Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+AuthenticationMechanism</p></td>
<td><p>Type of authentication used in the test. Allowed values are:</p>
<p>* TrustedServer</p>
<p>* Negotiate</p>
<p>* ClientCertificate</p>
<p>* LiveID</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>OutLoggerVariable</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>When present, detailed output from running the cmdlet will be stored in the specified variable. This variable includes a pair of methods – ToHTML and ToXML – that can then be used to save that output to either an HTML or an XML file.</p>
<p>To store output in a logger variable named $TestOutput use the following syntax:</p>
<p>-OutLoggerVariable TestOutput</p>
<p>Note: Do not use prepend a $ character when specifying the variable name.To save the information stored in the logger variable to an HTML file, use a command similar to this:</p>
<p>$TestOutput.ToHTML() &gt; C:\Logs\TestOutput.html</p>
<p>To save the information stored in the logger variable to an XML file, use a command similar to this:</p>
<p>$TestOutput.ToXML() &gt; C:\Logs\TestOutput.xml</p></td>
</tr>
<tr class="even">
<td><p><em>OutVerboseVariable</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax:</p>
<p>-OutVerboseVariable TestOutput</p>
<p>Do not prepend a $ character when specifying the variable name.</p></td>
</tr>
<tr class="odd">
<td><p><em>RegistrarPort</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Int32</p></td>
<td><p>SIP port used by the Registrar service. This parameter is not required if the Registrar uses the default port 5061.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetPstnPhoneNumber</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>Phone number for a PSTN telephone that will be used to verify that PSTN users can join the dial-in conference. For example:</p>
<p>-TargetPstnPhoneNumber &quot;+12065551219&quot;</p>
<p>Note that TargetPstnPhoneNumber should only be included when you are using the VerifyConferenceJoinType parameter.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserSipAddress</em></p></td>
<td><p>Optional</p></td>
<td><p>System.String</p></td>
<td><p>SIP address for user account to be tested. For example: -UserSipAddress &quot;sip:kenmyer@litwareinc.com&quot;. The UserSipAddress parameter must reference the same user account as UserCredential. This parameter is not required if you are conducting the test using the health monitoring configuration settings.</p></td>
</tr>
<tr class="even">
<td><p><em>VerifyConferenceJoin</em></p></td>
<td><p>Optional</p></td>
<td><p>System.Boolean</p></td>
<td><p>When set to True, verifies that the dial-in conference can joined by using a PSTN telephone. When performing this test you can optionally include the TargetPstnPhoneNumber. If you do that, TargetPstnPhoneNumber must specify the PSTN phone to be used for joining the conference. If TargetPstnPhoneNumber is not included then the <strong>Test-CsDialInConferencing</strong> cmdlet will use dial-in phone numbers preassigned to the appropriate dial-in conferencing region.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Test-CsDialInConferencing** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Test-CsDialInConferencing** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.

</div>

<div>

## See Also


[Test-CsAVConference](test-csavconference.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

