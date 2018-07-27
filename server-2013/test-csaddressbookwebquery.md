---
title: Test-CsAddressBookWebQuery
TOCTitle: Test-CsAddressBookWebQuery
ms:assetid: 9753dcba-83b3-437b-98f0-2806305a5bbb
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398773(v=OCS.15)
ms:contentKeyID: 48184863
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Test-CsAddressBookWebQuery

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-25_

Tests the ability of a user to search for, and return, information from the Address Book by using the Address Book Web Query service. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Test-CsAddressBookWebQuery -UserCredential <PSCredential> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-External <SwitchParameter>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsAddressBookWebQuery -TargetUri <String> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-WebCredential <PSCredential>] <COMMON PARAMETERS>

    Test-CsAddressBookWebQuery -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-External <SwitchParameter>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [-TargetSipAddress <String>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 tests the Address Book Web Query service for the pool atl-cs-001.litwareinc.com by searching for the contact with the SIP Address sip:kenmyer@litwareinc.com. This command will work only if test users have been defined for the pool atl-cs-001.litwareinc.com. If it has, then the command will run under the credentials of the first test user in the defined for the pool.

If test users have not been defined, then the command will fail. If you have not defined test users for a pool then you must include the UserSipAddress parameter and the credentials of the user under which the command should be run.

    Test-CsAddressBookWebQuery -TargetFqdn atl-cs-001.litwareinc.com  -TargetSipAddress "sip:kenmyer@litwareinc.com"

</div>

<div>

## EXAMPLE 2

The commands shown in Example 2 also test the availability of the Address Book Web Query service; in this case, however, the commands are running under the credentials of the user Ken Myer (litwareinc\\kenmyer). To do this, the first command uses the **Get-Credential** cmdlet to create a Windows PowerShell credential object containing the name and password of the user Ken Myer. (Because the logon name, litwareinc\\kenmyer, has been included as a parameter, the Windows PowerShell Credential Request dialog box will only require the administrator to enter the password for the Ken Myer account.) The resulting credential object is then stored in a variable named $cred1.

In the second command, the **Test-CsAddressBookWebQuery** cmdlet is used to test the Address Book Web Query service for the pool atl-cs-001.litwareinc.com. To run this command under Ken Myer’s user credentials, the UserCredential parameter is included, along with the parameter value $cred1. The command also uses the TargetSipAddress to specify that the cmdlet should search the Address Book for the contact with the SIP Address sip:kenmyer@litwareinc.com.

    $cred1 = Get-Credential "litwareinc\kenmyer"
    
    Test-CsAddressBookWebQuery -TargetFqdn atl-cs-001.litwareinc.com -UserCredential $cred1 -UserSipAddress "sip:kenmyer@litwareinc.com" -TargetSipAddress "sip:kenmyer@litwareinc.com"

</div>

<div>

## EXAMPLE 3

Example 3 shows how you can test the Address Book Web Query service for atl-cs-001.litwareinc.com. To do this, the **Test-CsAddressBookWebQuery** cmdlet is called along with three parameters: TargetUri, which specifies the URI of the Address Book Web Query service; UserSipAddress, which contains the Windows PowerShell SIP address of the user account being used in the test; and TargetSipAddress, which contains the SIP address of the user account being searched for.

    Test-CsAddressBookWebQuery -TargetUri https://atl-cs-001.litwareinc.com/groupexpansion -UserSipAddress "sip:packerman@litwareinc.com" -TargetSipAddress "sip:kenmyer@litwareinc.com"

</div>

</div>

<div>

## Detailed Description

The **Test-CsAddressBookWebQuery** cmdlet is an example of a "synthetic transaction." Synthetic transactions are used in Lync Server to verify that users are able to successfully complete common tasks such as logging on to the system, exchanging instant messages, or making calls to a phone located on the public switched telephone network (PSTN). These tests can be conducted manually by an administrator, or they can be automatically run by an application such as Microsoft System Center Operations Manager (formerly Microsoft Operations Manager).

Synthetic transactions are typically conducted in two different ways. Many administrators will use the **CsHealthMonitoringConfiguration** cmdlets to set up test users for each of their Registrar pools. These test users are a pair of users who have been preconfigured for use with synthetic transactions. (Typically these are test accounts and not accounts that belong to actual users.) With test users configured for a pool, administrators can run a synthetic transaction against that pool without having to specify the identities of (and supply the credentials for) the user accounts involved in the test.

Alternatively, administrators can run a synthetic transaction by using actual user accounts. For example, if two users are unable to exchange instant messages, an administrator could run a synthetic transaction using those two user accounts (as opposed to a pair of test accounts), and then try to diagnose and resolve the problem. If you decide to conduct a synthetic transaction using actual user accounts, you will need to supply the logon names and passwords for each user.

The **Test-CsAddressBookWebQuery** cmdlet provides a way for administrators to verify that users can use the Address Book Web Query service to search for a specific contact. When run, the **Test-CsAddressBookWebQuery** cmdlet will first connect to the Web Ticket service in order to be authenticated. If authentication is successful, the cmdlet will then connect to the Address Book Web Query service and search for the specified contact. If that contact is found, the cmdlet will attempt to return that information to the local computer. The test will be marked a success only if all of those steps can be completed.

Who can run this cmdlet: To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsAddressBookWebQuery"}

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
<td><p>String</p></td>
<td><p>Fully qualified domain name (FQDN) of the Registrar pool where the Address Book Web Query service is to be tested. For example: -TargetFqdn &quot;atl-cs-001.litwareinc.com&quot;.</p>
<p>Note that you cannot use both the TargetUri parameter and the TargetFqdn parameter in the same command.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetUri</em></p></td>
<td><p>Required</p></td>
<td><p>String</p></td>
<td><p>Uniform Resource Identifier (URI) of the Address Book Web Query service. For example: -TargetUri &quot;https://atl-cs-001.litwareinc.com/groupexpansion&quot;.</p>
<p>Note that you cannot use both the TargetUri parameter and the TargetFqdn parameter in the same command.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserCredential</em></p></td>
<td><p>Required</p></td>
<td><p>PSCredential</p></td>
<td><p>User credential object for the user account to be used in the test. The value passed to UserCredential should be an object reference obtained by using the <strong>Get-Credential</strong> cmdlet. For example, this code returns a credentials object for the user litwareinc\kenmyer and stores that object in a variable named</p>
<p>$x: $x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>You need to supply the user password when running this command.</p></td>
</tr>
<tr class="even">
<td><p><em>Authentication</em></p></td>
<td><p>Optional</p></td>
<td><p>SipSyntheticTransaction AuthenticationMechanism</p></td>
<td><p>Type of authentication used in the test. Allowed values are:</p>
<p>* TrustedServer</p>
<p>* Negotiate</p>
<p>* ClientCertificate</p>
<p>* LiveID</p></td>
</tr>
<tr class="odd">
<td><p><em>External</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Enables you to verify that external users can use the Address Book Web Query service.</p></td>
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
<p>Note: Do not use prepend a $ character when specifying the variable name.To save the information stored in the logger variable to an HTML file, use a command similar to this:</p>
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
<td><p><em>RegistrarPort</em></p></td>
<td><p>Optional</p></td>
<td><p>Int32</p></td>
<td><p>SIP port used by the Registrar service. This parameter is not required if the Registrar uses the default port 5061.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetSipAddress</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>SIP address of the contact expected to be returned by the Address Book Web Query service. For example: -TargetSipAddress &quot;sip:kenmyer@litwareinc.com&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserSipAddress</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>SIP address of the user to be used in the test. If this parameter is not specified then the <strong>Test-CsAddressBookWebQuery</strong> cmdlet will conduct its checks by using health monitoring configuration settings for the pool being tested.</p></td>
</tr>
<tr class="even">
<td><p><em>WebCredential</em></p></td>
<td><p>Optional</p></td>
<td><p>PSCredential</p></td>
<td><p>An object containing user credentials for accessing the Location Information service. This object can be retrieved by calling the <strong>Get-Credential</strong> cmdlet and supplying the appropriate credentials.</p>
<p>This parameter is required if the TargetUri and UserSipAddress parameters are specified, and the computer on which the command is run does not have a server certificate.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Input Types

None. The **Test-CsAddressBookWebQuery** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Test-CsAddressBookWebQuery** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.

</div>

<div>

## See Also


[Test-CsAddressBookService](test-csaddressbookservice.md)  
[Update-CsAddressBook](update-csaddressbook.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

