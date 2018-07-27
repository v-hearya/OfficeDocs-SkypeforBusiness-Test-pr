---
title: Test-CsAddressBookService
TOCTitle: Test-CsAddressBookService
ms:assetid: 8398c9ea-eaab-4a4d-9e09-473ea2b27e22
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398661(v=OCS.15)
ms:contentKeyID: 48184684
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Test-CsAddressBookService

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-25_

Tests the ability of a user to access the server that hosts the Address Book Download Web service. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Test-CsAddressBookService -UserCredential <PSCredential> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-External <SwitchParameter>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsAddressBookService -TargetUri <String> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-WebCredential <PSCredential>] <COMMON PARAMETERS>

    Test-CsAddressBookService -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-External <SwitchParameter>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

Example 1 tests the Address Book Download Web service for the pool atl-cs-001.litwareinc.com. This command tests the Address Book Download Web service by using test users preconfigured for the pool atl-cs-001.litwareinc.com.

    Test-CsAddressBookService -TargetFqdn atl-cs-001.litwareinc.com 

</div>

<div>

## EXAMPLE 2

The commands shown in Example 2 also test the availability of the server that runs the Address Book Download Web service; in this case, however, the commands are running under the credentials for the user Ken Myer (litwareinc\\kenmyer). To do this, the first command uses the **Get-Credential** cmdlet to create a Windows PowerShell credential object containing the name and password of the user Ken Myer. (Because the logon name -- litwareinc\\kenmyer -- has been included as a parameter, the Windows PowerShell Credential Request dialog box only requires the administrator to enter the password for the Ken Myer account.) The resulting credential object is then stored in a variable named $cred1.

In the second command, the **Test-CsAddressBookService** cmdlet is used to test the Address Book Download Web service for the pool atl-cs-001.litwareinc.com. To run this command under Ken Myer’s user credentials, the UserCredential parameter is included, along with the parameter value $cred1. In addition, Ken’s SIP address must be supplied using the UserSipAddress parameter.

    $cred1 = Get-Credential "litwareinc\kenmyer"
    
    Test-CsAddressBookService -TargetFqdn atl-cs-001.litwareinc.com -UserCredential $cred1 -UserSipAddress "sip:kenmyer@litwareinc.com"

</div>

<div>

## EXAMPLE 3

Example 3 shows how you can test the Address Book Download Web service for atl-cs-001.litwareinc.com. To do this, the **Test-CsAddressBookService** cmdlet is called along with two parameters: TargetUri, which specifies the URI of the Address Book Download Web service; and UserSipAddress, which contains the Windows PowerShell SIP address for the user account being used in the test.

``` 


Test-CsAddressBookService -TargetUri https://atl-cs-001.litwareinc.com/abs/handler -UserSipAddress "sip:kenmyer@litwareinc.com"
```

</div>

</div>

<div>

## Detailed Description

The **Test-CsAddressBookService** cmdlet is an example of a "synthetic transaction." Synthetic transactions are used in Lync Server to verify that users are able to successfully complete common tasks such as logging on to the system, exchanging instant messages, or making calls to a phone located on the public switched telephone network (PSTN). These tests can be conducted manually by an administrator, or they can be automatically run by an application such as Microsoft System Center Operations Manager (formerly Microsoft Operations Manager).

Synthetic transactions are typically conducted in two different ways. Many administrators will use the **CsHealthMonitoringConfiguration** cmdlets to set up test users for each of their Registrar pools. These test users are a pair of users who have been preconfigured for use with synthetic transactions. (Typically these are test accounts and not accounts that belong to actual users.) With test users configured for a pool, administrators can run a synthetic transaction against that pool without having to specify the identities of (and supply the credentials for) the user accounts involved in the test.

Alternatively, administrators can run a synthetic transaction by using actual user accounts. For example, if two users are unable to exchange instant messages, an administrator could run a synthetic transaction using those two user accounts (as opposed to a pair of test accounts), and then try to diagnose and resolve the problem. If you decide to conduct a synthetic transaction using actual user accounts, you will need to supply the logon names and passwords for each user.

The **Test-CsAddressBookService** cmdlet provides a way for you to verify that a user can connect to the Address Book Download Web service. When run, the **Test-CsAddressBookService** cmdlet connects to the Address Book Download Web service on the specified pool and requests the location of the Address Book files. If the Address Book Download Web service supplies that location, the test is considered successful. If the request is denied, then the test is considered a failure.

You can test the Address Book Download Web service in two different ways: by testing the service itself or by testing the associated Web service.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Test-CsAddressBookService** cmdlet: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsAddressBookService"}

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
<td><p>Fully qualified domain name (FQDN) of the Registrar pool where the Address Book Download Web service is to be tested. For example: -TargetFqdn &quot;atl-cs-001.litwareinc.com&quot;.</p>
<p>You cannot use both the TargetUri parameter and the TargetFqdn parameter in the same command.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetUri</em></p></td>
<td><p>Required</p></td>
<td><p>String</p></td>
<td><p>Uniform Resource Identifier (URI) of the Address Book Web Query service. For example: -TargetUri &quot;https://atl-cs-001.litwareinc.com/abs/handler&quot;.</p>
<p>You cannot use both the TargetUri parameter and the TargetFqdn parameter in the same command.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserCredential</em></p></td>
<td><p>Required</p></td>
<td><p>PSCredential</p></td>
<td><p>User credential object for the user account to be used in the test. The value passed to UserCredential should be an object reference obtained by using the <strong>Get-Credential</strong> cmdlet. For example, this code returns a credentials object for the user litwareinc\kenmyer and stores that object in a variable named $x:</p>
<p>$x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
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
<td><p>Enables you to verify that external users can use the Address Book Download Web service.</p></td>
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
<td><p><em>UserSipAddress</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>SIP address of the user to be used in the test. If this parameter is not specified then <strong>Test-CsAddressBookService</strong> will conduct its checks by using the account of the logged-in user.</p></td>
</tr>
<tr class="odd">
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

None. The **Test-CsAddressBookService** cmdlet does not accept pipelined input.

</div>

<div>

## Return Types

The **Test-CsAddressBookService** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.

</div>

<div>

## See Also


[Test-CsAddressBookWebQuery](test-csaddressbookwebquery.md)  
[Update-CsAddressBook](update-csaddressbook.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

