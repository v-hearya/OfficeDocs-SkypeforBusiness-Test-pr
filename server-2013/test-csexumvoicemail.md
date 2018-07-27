---
title: Test-CsExUMVoiceMail
TOCTitle: Test-CsExUMVoiceMail
ms:assetid: 88734ae8-1339-4080-a4bb-544181f6d1d2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205058(v=OCS.15)
ms:contentKeyID: 48184728
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Test-CsExUMVoiceMail

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-25_

Verifies that a user can connect to Exchange Unified Messaging and leave a voice mail message for another user. This cmdlet was introduced in Lync Server 2013.

<div>

## Syntax

    Test-CsExUMVoiceMail -ReceiverSipAddress <String> -SenderCredential <PSCredential> -SenderSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] [-WaveFile <String>] <COMMON PARAMETERS>

    Test-CsExUMVoiceMail -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-ReceiverSipAddress <String>] [-RegistrarPort <Int32>] [-SenderSipAddress <String>] [-WaveFile <String>] <COMMON PARAMETERS>

    Test-CsExUMVoiceMail [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>]

</div>

<span id="Examples"></span>

<div>

## Examples

<div>

## Example 1

The preceding example tests Exchange Unified Messaging voice mail connectivity for the pool atl-cs-001.litwareinc.com. This command will work only if test users have been defined for the pool atl-cs-001.litwareinc.com. If they have, then the command will determine whether or not the first test user is able to use Unified Messaging voice mail. If test users have not been configured for the pool then the command will fail.

    Test-CsExUMVoiceMail -TargetFqdn "atl-cs-001.litwareinc.com" -ReceiverSipAddress "sip:kenmyer@litwareinc.com"

</div>

<div>

## Example 2

The commands shown in Example 2 test Exchange Unified Messaging voice mail connectivity for the user litwareinc\\kenmyer. To do this, the first command in the example uses the **Get-Credential** cmdlet to create a Windows PowerShell command-line interface credentials object for the user litwareinc\\kenmyer. Note that you must supply the password for this account in order to create a valid credentials object and to ensure that the **Test-CsExUMVoiceMail** cmdlet can carry out its check.

The second command in the example uses the supplied credentials object ($x) and the SIP address of the user litwareinc\\kenmyer in order to determine whether or this user can connect to Exchange Unified Messaging voice mail.

    $credential = Get-Credential "litwareinc\pilar"
    
    Test-CsExUMVoiceMail -TargetFqdn "atl-cs-001.litwareinc.com" -ReceiverSipAddress "sip:kenmyer@litwareinc.com" -SenderSipAddress "sip:pilar@litwareinc.com" -SenderCredential $credential

</div>

<div>

## Example 3

The command shown in Example 3 is a variation of the command shown in Example 1; in this case, however, the OutLoggerVariable parameter is included in order to generate a detailed log of every step undertaken by the **Test-CsExUMVoiceMail** cmdlet, as well as the success or failure of each of those steps. To do this, the OutLoggerVariable parameter is added along with the parameter value ExumText; that causes detailed logging information to be stored in a variable named $ExumTest. In the final command in the example, the ToXML() method is used to convert the log information to XML format. That XML data is then written to a file named C:\\Logs\\VoicemailTest.xml by using the Out-File cmdlet.

    Test-CsExUMVoiceMail -TargetFqdn "atl-cs-001.litwareinc.com" -ReceiverSipAddress "sip:kenmyer@litwareinc.com" -OutLoggerVariable VoicemailTest
    
    $VoicemailTest.ToXML() | Out-File C:\Logs\VoicemailTest.xml

</div>

</div>

<span id="DetailedDescription"></span>

<div>

## Detailed Description

The **Test-CsExUMVoiceMail** cmdlet enables administrators to verify that a user can access, and make use of, the Microsoft Exchange Server 2013 unified messaging service. To do this, the cmdlet connects to the unified messaging service and leaves a voice mail in the specified mailbox. This can be a system-supplied voice mail, or it can be a custom .WAV file that you have recorded yourself.

To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsExUMVoiceMail"}

**Lync Server Control Panel:** The functions carried out by the Test-CsExUMVoiceMail cmdlet are not available in the Lync Server Control Panel.

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
<td><p><em>SenderCredential</em></p></td>
<td><p>Required</p></td>
<td><p>PSCredential</p></td>
<td><p>User credential object for the user account that will be leaving the voicemail message. The value passed to SenderCredential must be an object reference obtained by using the <strong>Get-Credential</strong> cmdlet. For example, this code returns a credentials object for the user litwareinc\kenmyer and stores that object in a variable named $x:</p>
<p>$x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>You need to supply the user password when running this command.</p>
<p>The sender credential is not required if you are running the test under the health monitoring configuration settings for the pool.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetFqdn</em></p></td>
<td><p>Required</p></td>
<td><p>String</p></td>
<td><p>Fully qualified domain name (FQDN) of the pool to be tested. For example:</p>
<p>-TargetFqdn atl-cs-001.litwareinc.com</p></td>
</tr>
<tr class="odd">
<td><p><em>Authentication</em></p></td>
<td><p>Optional</p></td>
<td><p>SipSyntheticTransaction AuthenticationMechanism</p></td>
<td><p>Type of authentication used when running the test. Allowed values are:</p>
<p>* TrustedServer</p>
<p>* Negotiate</p>
<p>* ClientCertificate</p>
<p>* LiveID</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suppresses the display of any non-fatal error message that might occur when running the command.</p></td>
</tr>
<tr class="odd">
<td><p><em>OutLoggerVariable</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>When present, detailed output from running the cmdlet will be stored in the specified variable. This variable includes a pair of methods – ToHTML and ToXML – that can then be used to save that output to either an HTML or an XML file.</p>
<p>To store output in a logger variable named $TestOutput use the following syntax:</p>
<p>-OutLoggerVariable TestOutput</p>
<p>Note: Do not use prepend a $ character when specifying the variable name.</p>
<p>To save the information stored in the logger variable to an HTML file, use a command similar to this:</p>
<p>$TestOutput.ToHTML() &gt; C:\Logs\TestOutput.html</p>
<p>To save the information stored in the logger variable to an XML file, use a command similar to this:</p>
<p>$TestOutput.ToXML() &gt; C:\Logs\TestOutput.xml</p></td>
</tr>
<tr class="even">
<td><p><em>OutVerboseVariable</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax:</p>
<p>-OutVerboseVariable TestOutput</p>
<p>Do not prepend a $ character when specifying the variable name.</p></td>
</tr>
<tr class="odd">
<td><p><em>ReceiverSipAddress</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>SIP address for the user account that should receive the test voice mail (this must be a different SIP address than the SIP address used for the sender). For example:</p>
<p>-ReceiverSipAddress &quot;sip:pilar@litwareinc.com&quot;</p>
<p>You do not have to include credentials for the voicemail recipient.</p></td>
</tr>
<tr class="even">
<td><p><em>RegistrarPort</em></p></td>
<td><p>Optional</p></td>
<td><p>Int32</p></td>
<td><p>SIP port used by the Registrar service. This parameter is not required if the Registrar uses the default port 5061.</p></td>
</tr>
<tr class="odd">
<td><p><em>SenderSipAddress</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>SIP address for the user account that will be leaving the voicemail message (this must be a different SIP address than the SIP address used for the receiver). For example:</p>
<p>-SenderSipAddress &quot;sip:kenmyer@litwareinc.com&quot;</p>
<p>The SenderSIPAddress parameter must reference the same user account as SenderCredential.</p>
<p>The SIP address is not required if you are running the test under the health monitoring configuration settings for the pool.</p></td>
</tr>
<tr class="even">
<td><p><em>WaveFile</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>Path to .WAV audio file that can be used when testing the voice mail service. If this parameter is included, the <strong>Test-CsExUMVoiceMail</strong> cmdlet will play the specified .WAV file when connecting to Exchange voicemail. If this parameter is not included, a default audio file will be played instead.</p></td>
</tr>
</tbody>
</table>


</div>

<span id="InputTypes"></span>

<div>

## Input Types

None. The Test-CsExUMVoiceMail cmdlet does not accept pipelined input.

</div>

<span id="ReturnTypes"></span>

<div>

## Return Types

The **Test-CsExUMVoiceMail** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.

</div>

<div>

## See Also


[Test-CsExUMConnectivity](test-csexumconnectivity.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

