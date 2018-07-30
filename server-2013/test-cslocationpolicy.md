---
title: Test-CsLocationPolicy
TOCTitle: Test-CsLocationPolicy
ms:assetid: 49f7d148-d46d-4bcc-af9d-6a3a0fdde8ee
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425962(v=OCS.15)
ms:contentKeyID: 48184012
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Test-CsLocationPolicy

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-03-25_

Runs a test to determine the location policy that will be used based on the criteria specified in the parameter values. The location policy contains the settings that will determine whether and how Enhanced 9-1-1 (E9-1-1) will be applied. E9-1-1 enables those who answer 911 emergency calls to determine the caller’s geographic location. This cmdlet was introduced in Lync Server 2010.

<div>

## Syntax

    Test-CsLocationPolicy -UserCredential <PSCredential> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsLocationPolicy -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

    Test-CsLocationPolicy [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [-Subnet <String>]

</div>

<div>

## Examples

<div>

## EXAMPLE 1

This example determines the location policy of the current user (or currently configured user). The TargetFqdn is required.

    Test-CsLocationPolicy -TargetFqdn atl-cs-001.litwareinc.com 

</div>

<div>

## EXAMPLE 2

The first line in Example 2 is a call to the Windows PowerShell **Get-Credential** cmdlet. This cmdlet will retrieve user credentials and return them as a secure object. The only parameter supplied to this cmdlet is the user ID. Running this cmdlet will open a dialog box that is prepopulated with the user ID supplied and has a text box that allows you to type in the user password. These user credentials are saved to the variable $cred.

Line 2 calls the **Test-CsLocationPolicy** cmdlet. Just like in Example 1, we supply the target FQDN. However, in this example rather than using the preconfigured user, we’re going to run the test against the user with the SIP address kenmyer@litwareinc.com. We pass that value (with the sip: prefix) to the UserSipAddress parameter, and the credentials for that user (stored in the $cred variable) to the UserCredential parameter.

    $cred = Get-Credential "litwareinc\kenmyer"
    Test-CsLocationPolicy -TargetFqdn atl-cs-001.litwareinc.com -UserCredential $cred -UserSipAddress "sip:kenmyer@litwareinc.com"

</div>

<div>

## EXAMPLE 3

This example is similar to Example 2, but without the user credentials specified. When the **Test-CsLocationPolicy** cmdlet is called without specifying user credentials, the server certificate on the computer where this cmdlet is being run is used to authenticate and discover the user’s location policy. If the computer does not have a server certificate, you must specify credentials as shown in Example 2. To find out whether there is a server certificate on the computer, call the **Get-CsCertificate** cmdlet.

    Test-CsLocationPolicy -TargetFqdn atl-cs-001.litwareinc.com -UserSipAddress "sip:kenmyer@litwareinc.com"

</div>

<div>

## EXAMPLE 4

This example determines the location policy of the subnet with the subnet ID 172.15.11.0. If the subnet is not associated with a location policy, the location policy for the currently configured user will be retrieved.

Note: A location policy is set on a subnet by setting the LocationPolicy parameter of the **Set-CsNetworkSite** cmdlet to the location policy ID, and then setting the NetworkSiteId parameter of the **Set-CsNetworkSubnet** cmdlet to the ID of that site. For example:

Set-CsNetworkSite Portland –LocationPolicy Reno

Set-CsNetworkSubnet 175.15.11.0 –NetworkSiteID Portland

    Test-CsLocationPolicy -TargetFqdn atl-cs-001.litwareinc.com -Subnet 172.15.11.0

</div>

</div>

<div>

## Detailed Description

The location policy is used to apply settings that relate to E9-1-1 functionality and client location. The location policy determines whether a user is enabled for E9-1-1, and if so what the behavior is of an emergency call. For example, you can use the location policy to define what number constitutes an emergency call (911 in the United States), whether corporate security should be automatically notified, and how the call should be routed. This cmdlet returns information about the location policy that will be used when calls are made from a particular client on a specific pool, subnet, switch, or wireless access point.

If a user is not specified in the call to this cmdlet, the currently configured user will be tested. To find the currently configured user, call the **Get-CsHealthMonitoringConfiguration** cmdlet. To set the configured user, call the **Set-CsHealthMonitoringConfiguration** cmdlet.

If a location policy was found for the user or subnet, the test will succeed. Information returned by default includes the name of the location policy (if a per-user policy is assigned) and whether the user or subnet is enabled for E9-1-1. Include the Windows PowerShell common parameter Verbose to retrieve additional information about the test.

You can test location policies on users or on network subnets. If you run the test against a subnet (by specifying a value for the Subnet parameter), the cmdlet will attempt to resolve the location policy for that subnet. If no location policy is assigned to the subnet, the location policy for the configured user will be retrieved. If the subnet policy is retrieved successfully, the output will include a LocationPolicyTagID value beginning with subnet-tagid. If a location policy for the subnet was not found, the LocationPolicyTagID will begin with user-tagid.

Who can run this cmdlet: By default, members of the following groups are authorized to run the **Test-CsLocationPolicy** cmdlet locally: RTCUniversalServerAdmins. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Windows PowerShell prompt:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsLocationPolicy"}

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
<td><p>The fully qualified domain name (FQDN) of the pool on which the specified user or subnet is homed. (If no user is specified, the preconfigured or current user will be assumed.)</p></td>
</tr>
<tr class="even">
<td><p><em>UserCredential</em></p></td>
<td><p>Required</p></td>
<td><p>PSCredential</p></td>
<td><p>An object containing the user ID and password of the user account where the location policy is being tested. A credential object can be retrieved by calling the <strong>Get-Credential</strong> cmdlet, filling in the appropriate information, and saving the output to a variable.</p></td>
</tr>
<tr class="odd">
<td><p><em>Authentication</em></p></td>
<td><p>Optional</p></td>
<td><p>SipSyntheticTransaction AuthenticationMechanism</p></td>
<td><p>Type of authentication used in the test. Allowed values are:</p>
<p>* TrustedServer</p>
<p>* Negotiate</p>
<p>* ClientCertificate</p>
<p>* LiveID</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Optional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suppresses any confirmation prompts that would otherwise be displayed before making changes.</p></td>
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
<td><p>String</p></td>
<td><p>When present, detailed output from running the cmdlet will be stored in the specified variable. For example, to store output in a variable named $TestOutput use the following syntax:</p>
<p>-OutVerboseVariable TestOutput</p>
<p>Do not prepend a $ character when specifying the variable name.</p></td>
</tr>
<tr class="odd">
<td><p><em>RegistrarPort</em></p></td>
<td><p>Optional</p></td>
<td><p>Int32</p></td>
<td><p>The port number of the Registrar service.</p></td>
</tr>
<tr class="even">
<td><p><em>Subnet</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The ID (the IP address) of the network subnet for which you want to test the location policy.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserSipAddress</em></p></td>
<td><p>Optional</p></td>
<td><p>String</p></td>
<td><p>The SIP address of the user whose location policy you want to test. This must be in the format sip:&lt;user id&gt;, for example, sip:kenmyer@litwareinc.com.</p></td>
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

The **Test-CsLocationPolicy** cmdlet returns an instance of the Microsoft.Rtc.SyntheticTransactions.TaskOutput object.

</div>

<div>

## See Also


[New-CsLocationPolicy](new-cslocationpolicy.md)  
[Remove-CsLocationPolicy](remove-cslocationpolicy.md)  
[Set-CsLocationPolicy](set-cslocationpolicy.md)  
[Get-CsLocationPolicy](get-cslocationpolicy.md)  
[Grant-CsLocationPolicy](grant-cslocationpolicy.md)  
[Get-CsHealthMonitoringConfiguration](get-cshealthmonitoringconfiguration.md)  
[Set-CsHealthMonitoringConfiguration](set-cshealthmonitoringconfiguration.md)  
[Set-CsNetworkSite](set-csnetworksite.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

