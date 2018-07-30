---
title: Test-CsLisConfiguration
TOCTitle: Test-CsLisConfiguration
ms:assetid: 6983d42e-6b93-4365-b0f1-81031d6e251b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398497(v=OCS.15)
ms:contentKeyID: 48184385
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Test-CsLisConfiguration

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-25_

Tests the Location Information Server (LIS) configuration. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Test-CsLisConfiguration -UserCredential <PSCredential> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-External <SwitchParameter>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsLisConfiguration -TargetUri <String> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-WebCredential <PSCredential>] <COMMON PARAMETERS>

    Test-CsLisConfiguration -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-External <SwitchParameter>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-BssId <String>] [-ChassisId <String>] [-Force <SwitchParameter>] [-Mac <String>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [-PortId <String>] [-PortIdSubType <InterfaceAlias | InterfaceName | LocallyAssigned>] [-Subnet <String>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example tests the LIS configuration at the FQDN atl-cs-001.litwareinc.com. The test will be successful if a connection can be made with the current user credentials to the LIS web service at that FQDN. If a location can be found that maps to the subnet IP address 192.168.0.0, then that location address will be returned.

For this command to succeed, a health monitoring configuration containing synthetic transaction users must exist. To see if a health monitoring configuration exists, run the **Get-CsHealthMonitoringConfiguration** cmdlet. To create a new health monitoring configuration, run the **New-CsHealthMonitoringConfiguration** cmdlet.

    Test-CsLisConfiguration -TargetFqdn atl-cs-001.litwareinc.com -Subnet 192.168.0.0

</div>

<div>

## EXAMPLE 2

This example is identical to Example 1 but with the addition of the UserSipAddress parameter. Use this command when no synthetic transaction users have been set up, but where the computer on which the command is running has a server certificate.

    Test-CsLisConfiguration -TargetFqdn atl-cs-001.litwareinc.com -Subnet 192.168.0.0 -UserSipAddress sip:kmyer@litwareinc.com

</div>

<div>

## EXAMPLE 3

The first line of this example calls a Windows PowerShell cmdlet, the **Get-Credential** cmdlet, which prompts the user for a user ID and password. This information is stored in an encrypted fashion in the variable $cred.

The second line is identical to the command in Example 2 but with the addition of the UserSipAddress parameter. Use this command when no synthetic transaction users have been set up, and where the computer on which the command is running does not have a server certificate.

    $cred = Get-Credential
    Test-CsLisConfiguration -TargetFqdn atl-cs-001.litwareinc.com -Subnet 192.168.0.0 -UserSipAddress sip:kmyer@litwareinc.com -UserCredential $cred

</div>

<div>

## EXAMPLE 4

The first line of this example calls the **Get-Credential** cmdlet, which prompts the user for a user ID and password. This information is stored in an encrypted fashion in the variable $cred.

Line 2 tests the LIS configuration by making a call to the web service URI (https://atl-cs-001.litwareinc.com/locationinformation/lisservice.svc) based on the SIP address of the remote user (sip:kmyer@litwareinc.com), and using the credentials we obtained in line 1 by passing them to the WebCredential parameter. The test will be successful if a connection can be made with the given user credentials to the LIS web service at that URI. If a location can be found that maps to the subnet IP address 192.168.0.0, the MAC address 0A-23-00-00-00-AA or the Port ID 4500 and ChassisId 0A-23-00-00-00-AA, that location address will be returned.

Use this command when the computer on which the command is running does not have a server certificate.

    $cred = Get-Credential
    Test-CsLisConfiguration -TargetUri https://atl-cs-001.litwareinc.com/locationinformation/lisservice.svc -UserSipAddress sip:kmyer@litwareinc.com -WebCredential $cred -Subnet 192.168.0.0 -Mac 0A-23-00-00-00-AA -PortId 4500 -ChassisId 0A-23-00-00-00-AA

</div>

<div>

## EXAMPLE 5

This example is identical to Example 4, except that the command does not use the WebCredential parameter (and therefore also does not call the **Get-Credential** cmdlet). Use this command when the computer on which the command is running has a server certificate.

    Test-CsLisConfiguration -TargetUri https://atl-cs-001.litwareinc.com/locationinformation/lisservice.svc -UserSipAddress sip:kmyer@litwareinc.com -Subnet 192.168.0.0 -Mac 0A-23-00-00-00-AA -PortId 4500 -ChassisId 0A-23-00-00-00-AA

</div>

</div>

<div>

## Detailed Description

This cmdlet determines whether the Location Information Server (LIS) web service can be contacted based on the information in the supplied parameters. If the web service can be contacted and a location is found that corresponds to any of the supplied parameters, the test is considered to have passed and the location will be displayed. Even if the location is not found, if the web service can be contacted the test will return a pass, but with no location information. In addition, if you call this cmdlet without supplying any of the optional parameters, the test will still pass as long as the web service can be contacted; however, again, no location information will be returned.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Test-CsLisConfiguration** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsConfiguration"}

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
<td><p>The fully qualified domain name (FQDN) (in the form server.litwareinc.com) of the server against which you want to run the test.</p>
<p>This parameter is required unless you specify the TargetUri parameter, in which case you cannot specify a TargetFqdn.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetUri</em></p></td>
<td><p>Required</p></td>
<td><p>String</p></td>
<td><p>The Uniform Resource Identifier (URI) of the Location Information service. You can retrieve the URI of the Location Information service by running the following command: Get-CsService –WebServer | Select-Object LIServiceInternalUri</p>
<p>If you specify a value for this parameter, the UserSipAddress parameter is also required. If the computer you are running the command on does not have a server certificate, you must also specify a value for the WebCredential parameter.</p>
<p>This parameter is required unless you specify the TargetFqdn parameter.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserCredential</em></p></td>
<td><p>Required</p></td>
<td><p>PSCredential</p></td>
<td><p>An object containing user credentials for accessing the Location Information service. This object can be retrieved by calling the <strong>Get-Credential</strong> cmdlet and supplying the appropriate credentials.</p>
<p>This parameter is required if the TargetFqdn and UserSipAddress parameters are specified, and if the computer from which you’re running the cmdlet does not have a server certificate.</p></td>
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
<td><p><em>BssId</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The Basic Service Set Identifier (BSSID) of a wireless access point. This value must be in the form nn-nn-nn-nn-nn-nn, such as 12-34-56-78-90-ab.</p></td>
</tr>
<tr class="even">
<td><p><em>ChassisId</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The Media Access Control (MAC) address of a network switch. This value must be in the form nn-nn-nn-nn-nn-nn, such as 12-34-56-78-90-ab, or an IP address.</p></td>
</tr>
<tr class="odd">
<td><p><em>External</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>This parameter is not supported for Location Information Server.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suppresses any confirmation prompts that would otherwise be displayed before making changes.</p></td>
</tr>
<tr class="odd">
<td><p><em>Mac</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The MAC address of the port switch. This value must be in the form nn-nn-nn-nn-nn-nn, such as 12-34-56-78-90-ab.</p></td>
</tr>
<tr class="even">
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
<tr class="odd">
<td><p><em>OutVerboseVariable</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax:</p>
<p>-OutVerboseVariable TestOutput</p>
<p>Do not prepend a $ character when specifying the variable name.</p></td>
</tr>
<tr class="even">
<td><p><em>PortId</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The ID of the port associated with the location to test. This can also contain a MAC address or IP address.</p></td>
</tr>
<tr class="odd">
<td><p><em>PortIdSubType</em></p></td>
<td><p>Optional</p></td>
<td><p>PortIDSubType</p></td>
<td><p>The subtype of the port. This value can be entered as a numeric value or a string, but it must be a valid subtype. Valid subtypes are:</p>
<p>1: InterfaceAlias</p>
<p>5: InterfaceName</p>
<p>7: LocallyAssigned</p></td>
</tr>
<tr class="even">
<td><p><em>RegistrarPort</em></p></td>
<td><p>Optional</p></td>
<td><p>Int32</p></td>
<td><p>The port number of the Registrar service.</p></td>
</tr>
<tr class="odd">
<td><p><em>Subnet</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The IP address of a subnet. This value should be entered as an IPv4 address (digits separated by periods, such as 192.0.2.0).</p></td>
</tr>
<tr class="even">
<td><p><em>UserSipAddress</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The SIP address of a remote user.</p>
<p>If you specify a value for this parameter, the TargetFqdn or TargetUri parameter is also required.</p>
<p>This parameter is required when you specify the TargetFqdn parameter only if you have not set up synthetic transactions users. To see if synthetic transaction users have been set up, run the <strong>Get-CsHealthMonitoringConfiguration</strong> cmdlet.</p></td>
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

None.

</div>

<div>

## Return Types

The **Test-CsLisConfiguration** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.

</div>

<div>

## See Also


[Debug-CsLisConfiguration](debug-cslisconfiguration.md)  
[Publish-CsLisConfiguration](publish-cslisconfiguration.md)  
[Unpublish-CsLisConfiguration](unpublish-cslisconfiguration.md)  
[Import-CsLisConfiguration](import-cslisconfiguration.md)  
[Export-CsLisConfiguration](export-cslisconfiguration.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

