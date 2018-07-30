---
title: 'Lync Server 2013: Server roles and services cmdlets'
TOCTitle: Server roles and services cmdlets
ms:assetid: ff3561de-043e-4071-88f7-8de3cded52f6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg415683(v=OCS.15)
ms:contentKeyID: 48185971
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Server roles and services cmdlets in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-29_

Many Microsoft Lync Server 2013 components run as server roles or as services. Lync Server 2013 ships with a number of cmdlets that enable you to manage these server roles and services.

<div>

## Server Roles and Services Cmdlets

Many (but not all) of the management tasks that apply to servers and service roles can be performed from the Lync Server Control Panel. For example, you can manage Archiving Server settings but not Address Book Server settings by using Lync Server Control Panel. However, all these tasks can be performed using cmdlets from the Lync Server Management Shell or from within a script; using a script enables you to automate certain tasks. The following is a list of cmdlets that relate directly to managing server roles and services:

**[Address Book Server cmdlets in Lync Server 2013](lync-server-2013-address-book-server-cmdlets.md)**

  - <span></span>  
    [Get-CsAddressBookConfiguration](get-csaddressbookconfiguration.md)

  - <span></span>  
    [New-CsAddressBookConfiguration](new-csaddressbookconfiguration.md)

  - <span></span>  
    [Remove-CsAddressBookConfiguration](remove-csaddressbookconfiguration.md)

  - <span></span>  
    [Set-CsAddressBookConfiguration](set-csaddressbookconfiguration.md)

<!-- end list -->

  - <span></span>  
    [Update-CsAddressBook](update-csaddressbook.md)

<!-- end list -->

  - <span></span>  
    [Debug-CsAddressBookReplication](debug-csaddressbookreplication.md)

<!-- end list -->

  - <span></span>  
    [Test-CsAddressBookService](test-csaddressbookservice.md)

<!-- end list -->

  - <span></span>  
    [Test-CsAddressBookWebQuery](test-csaddressbookwebquery.md)

**[Archiving and Monitoring cmdlets in Lync Server 2013](lync-server-2013-archiving-and-monitoring-cmdlets.md)**

  - <span></span>  
    [Get-CsArchivingConfiguration](get-csarchivingconfiguration.md)

  - <span></span>  
    [New-CsArchivingConfiguration](new-csarchivingconfiguration.md)

  - <span></span>  
    [Remove-CsArchivingConfiguration](remove-csarchivingconfiguration.md)

  - <span></span>  
    [Set-CsArchivingConfiguration](set-csarchivingconfiguration.md)

<!-- end list -->

  - <span></span>  
    [Export-CsArchivingData](export-csarchivingdata.md)

<!-- end list -->

  - <span></span>  
    [Invoke-CsArchivingDatabasePurge](invoke-csarchivingdatabasepurge.md)

<!-- end list -->

  - <span></span>  
    [Get-CsArchivingPolicy](get-csarchivingpolicy.md)

  - <span></span>  
    [Grant-CsArchivingPolicy](grant-csarchivingpolicy.md)

  - <span></span>  
    [New-CsArchivingPolicy](new-csarchivingpolicy.md)

  - <span></span>  
    [Remove-CsArchivingPolicy](remove-csarchivingpolicy.md)

  - <span></span>  
    [Set-CsArchivingPolicy](set-csarchivingpolicy.md)

<!-- end list -->

  - <span></span>  
    [Set-CsArchivingServer](set-csarchivingserver.md)

<!-- end list -->

  - <span></span>  
    [Get-CsCdrConfiguration](get-cscdrconfiguration.md)

  - <span></span>  
    [New-CsCdrConfiguration](new-cscdrconfiguration.md)

  - <span></span>  
    [Remove-CsCdrConfiguration](remove-cscdrconfiguration.md)

  - <span></span>  
    [Set-CsCdrConfiguration](set-cscdrconfiguration.md)

<!-- end list -->

  - <span></span>  
    [Set-CsMonitoringServer](set-csmonitoringserver.md)

<!-- end list -->

  - <span></span>  
    [Get-CsQoEConfiguration](get-csqoeconfiguration.md)

  - <span></span>  
    [New-CsQoEConfiguration](new-csqoeconfiguration.md)

  - <span></span>  
    [Remove-CsQoEConfiguration](remove-csqoeconfiguration.md)

  - <span></span>  
    [Set-CsQoEConfiguration](set-csqoeconfiguration.md)

[Invoke-CsCdrDatabasePurge](invoke-cscdrdatabasepurge.md)

  - <span></span>  
    [Export-CsArchivingData](export-csarchivingdata.md)

<!-- end list -->

  - <span></span>  
    [Invoke-CsQoEDatabasePurge](invoke-csqoedatabasepurge.md)

<!-- end list -->

  - <span></span>  
    [Get-CsReportingConfiguration](get-csreportingconfiguration.md)

  - <span></span>  
    [New-CsReportingConfiguration](new-csreportingconfiguration.md)

  - <span></span>  
    [Remove-CsReportingConfiguration](remove-csreportingconfiguration.md)

  - <span></span>  
    [Set-CsReportingConfiguration](set-csreportingconfiguration.md)

<!-- end list -->

  - <span></span>  
    [Get-CsTestUserCredential](get-cstestusercredential.md)

  - <span></span>  
    [Remove-CsTestUserCredential](remove-cstestusercredential.md)

  - <span></span>  
    [Set-CsTestUserCredential](set-cstestusercredential.md)

<!-- end list -->

  - <span></span>  
    [Get-CsWatcherNodeConfiguration](get-cswatchernodeconfiguration.md)

  - <span></span>  
    [New-CsWatcherNodeConfiguration](new-cswatchernodeconfiguration.md)

  - <span></span>  
    [Remove-CsWatcherNodeConfiguration](remove-cswatchernodeconfiguration.md)

  - <span></span>  
    [Set-CsWatcherNodeConfiguration](set-cswatchernodeconfiguration.md)

  - <span></span>  
    [Test-CsWatcherNodeConfiguration](test-cswatchernodeconfiguration.md)

<!-- end list -->

  - <span></span>  
    [New-CsExtendedTest](new-csextendedtest.md)

**[Database and Management Server cmdlets in Lync Server 2013](lync-server-2013-database-and-management-server-cmdlets.md)**

  - <span></span>  
    [Get-CsConfigurationStoreLocation](get-csconfigurationstorelocation.md)

  - <span></span>  
    [Remove-CsConfigurationStoreLocation](remove-csconfigurationstorelocation.md)

  - <span></span>  
    [Set-CsConfigurationStoreLocation](set-csconfigurationstorelocation.md)

<!-- end list -->

  - <span></span>  
    [Install-CsDatabase](install-csdatabase.md)

  - <span></span>  
    [Test-CsDatabase](test-csdatabase.md)

  - <span></span>  
    [Uninstall-CsDatabase](uninstall-csdatabase.md)

<!-- end list -->

  - [Invoke-CsDatabaseFailover](invoke-csdatabasefailover.md)

<!-- end list -->

  - [Get-CsDatabaseMirrorState](get-csdatabasemirrorstate.md)

<!-- end list -->

  - [Install-CsMirrorDatabase](install-csmirrordatabase.md)

  - [Uninstall-CsMirrorDatabase](uninstall-csmirrordatabase.md)

<!-- end list -->

  - <span></span>  
    [Get-CsUserDatabaseState](get-csuserdatabasestate.md)

  - <span></span>  
    [Set-CsUserDatabaseState](set-csuserdatabasestate.md)

<!-- end list -->

  - <span></span>  
    [Update-CsUserDatabase](update-csuserdatabase.md)

<!-- end list -->

  - <span></span>  
    [Move-CsManagementServer](move-csmanagementserver.md)

  - <span></span>  
    [Set-CsManagementServer](set-csmanagementserver.md)

<!-- end list -->

  - [Invoke-CsManagementServerFailover](invoke-csmanagementserverfailover.md)

**[Edge Server cmdlets in Lync Server 2013](lync-server-2013-edge-server-cmdlets.md)**

  - <span></span>  
    [Get-CsAccessEdgeConfiguration](get-csaccessedgeconfiguration.md)

  - <span></span>  
    [Set-CsAccessEdgeConfiguration](set-csaccessedgeconfiguration.md)

<!-- end list -->

  - <span></span>  
    [Get-CsAVEdgeConfiguration](get-csavedgeconfiguration.md)

  - <span></span>  
    [New-CsAVEdgeConfiguration](new-csavedgeconfiguration.md)

  - <span></span>  
    [Remove-CsAVEdgeConfiguration](remove-csavedgeconfiguration.md)

  - <span></span>  
    [Set-CsAVEdgeConfiguration](set-csavedgeconfiguration.md)

<!-- end list -->

  - <span></span>  
    [Test-CsAVEdgeConnectivity](test-csavedgeconnectivity.md)

<!-- end list -->

  - <span></span>  
    [Set-CsEdgeServer](set-csedgeserver.md)

**[Other server role cmdlets in Lync Server 2013](lync-server-2013-other-server-role-cmdlets.md)**

  - <span></span>  
    [Set-CsConferenceServer](set-csconferenceserver.md)

<!-- end list -->

  - <span></span>  
    [Set-CsUserServer](set-csuserserver.md)

**[Registrar and Director cmdlets in Lync Server 2013](lync-server-2013-registrar-and-director-cmdlets.md)**

  - <span></span>  
    [Set-CsDirector](set-csdirector.md)

<!-- end list -->

  - <span></span>  
    [Reset-CsPoolRegistrarState](reset-cspoolregistrarstate.md)

<!-- end list -->

  - <span></span>  
    [Set-CsRegistrar](set-csregistrar.md)

<!-- end list -->

  - <span></span>  
    [Get-CsRegistrarConfiguration](get-csregistrarconfiguration.md)

  - <span></span>  
    [New-CsRegistrarConfiguration](new-csregistrarconfiguration.md)

  - <span></span>  
    [Remove-CsRegistrarConfiguration](remove-csregistrarconfiguration.md)

  - <span></span>  
    [Set-CsRegistrarConfiguration](set-csregistrarconfiguration.md)

<!-- end list -->

  - <span></span>  
    [Test-CsRegistration](test-csregistration.md)

**[Services cmdlets in Lync Server 2013](lync-server-2013-services-cmdlets.md)**

  - <span></span>  
    [Get-CsService](get-csservice.md)

<!-- end list -->

  - <span></span>  
    [Get-CsWindowsService](get-cswindowsservice.md)

  - <span></span>  
    [Start-CsWindowsService](start-cswindowsservice.md)

  - <span></span>  
    [Stop-CsWindowsService](stop-cswindowsservice.md)

**[Troubleshooting server roles and services cmdlets in Lync Server 2013](lync-server-2013-troubleshooting-server-roles-and-services-cmdlets.md)**

  - <span></span>  
    [Get-CsAudioTestServiceApplication](get-csaudiotestserviceapplication.md)

  - <span></span>  
    [Set-CsAudioTestServiceApplication](set-csaudiotestserviceapplication.md)

<!-- end list -->

  - <span></span>  
    [Get-CsHealthMonitoringConfiguration](get-cshealthmonitoringconfiguration.md)

  - <span></span>  
    [New-CsHealthMonitoringConfiguration](new-cshealthmonitoringconfiguration.md)

  - <span></span>  
    [Remove-CsHealthMonitoringConfiguration](remove-cshealthmonitoringconfiguration.md)

  - <span></span>  
    [Set-CsHealthMonitoringConfiguration](set-cshealthmonitoringconfiguration.md)

<!-- end list -->

  - <span></span>  
    [Get-CsDiagnosticConfiguration](get-csdiagnosticconfiguration.md)

  - <span></span>  
    [New-CsDiagnosticConfiguration](new-csdiagnosticconfiguration.md)

  - <span></span>  
    [Remove-CsDiagnosticConfiguration](remove-csdiagnosticconfiguration.md)

  - <span></span>  
    [Set-CsDiagnosticConfiguration](set-csdiagnosticconfiguration.md)

<!-- end list -->

  - <span></span>  
    [New-CsDiagnosticsFilter](new-csdiagnosticsfilter.md)

<!-- end list -->

  - <span></span>  
    [Get-CsDiagnosticHeaderConfiguration](get-csdiagnosticheaderconfiguration.md)

  - <span></span>  
    [New-CsDiagnosticHeaderConfiguration](new-csdiagnosticheaderconfiguration.md)

  - <span></span>  
    [Remove-CsDiagnosticHeaderConfiguration](remove-csdiagnosticheaderconfiguration.md)

  - <span></span>  
    [Set-CsDiagnosticHeaderConfiguration](set-csdiagnosticheaderconfiguration.md)

**[Web server and services cmdlets in Lync Server 2013](lync-server-2013-web-server-and-services-cmdlets.md)**

  - <span></span>  
    [New-CsSimpleUrl](new-cssimpleurl.md)

<!-- end list -->

  - <span></span>  
    [Get-CsSimpleUrlConfiguration](get-cssimpleurlconfiguration.md)

  - <span></span>  
    [New-CsSimpleUrlConfiguration](new-cssimpleurlconfiguration.md)

  - <span></span>  
    [Remove-CsSimpleUrlConfiguration](remove-cssimpleurlconfiguration.md)

  - <span></span>  
    [Set-CsSimpleUrlConfiguration](set-cssimpleurlconfiguration.md)

<!-- end list -->

  - <span></span>  
    [New-CsSimpleUrlEntry](new-cssimpleurlentry.md)

<!-- end list -->

  - <span></span>  
    [Set-CsWebServer](set-cswebserver.md)

<!-- end list -->

  - <span></span>  
    [Get-CsWebServiceConfiguration](get-cswebserviceconfiguration.md)

  - <span></span>  
    [New-CsWebServiceConfiguration](new-cswebserviceconfiguration.md)

  - <span></span>  
    [Remove-CsWebServiceConfiguration](remove-cswebserviceconfiguration.md)

  - <span></span>  
    [Set-CsWebServiceConfiguration](set-cswebserviceconfiguration.md)

<!-- end list -->

  - <span></span>  
    [New-CsWebTrustedCACertificate](new-cswebtrustedcacertificate.md)

<!-- end list -->

  - <span></span>  
    [New-CsKerberosAccount](new-cskerberosaccount.md)

<!-- end list -->

  - <span></span>  
    [Get-CsKerberosAccountAssignment](get-cskerberosaccountassignment.md)

  - <span></span>  
    [New-CsKerberosAccountAssignment](new-cskerberosaccountassignment.md)

  - <span></span>  
    [Remove-CsKerberosAccountAssignment](remove-cskerberosaccountassignment.md)

  - <span></span>  
    [Set-CsKerberosAccountAssignment](set-cskerberosaccountassignment.md)

  - <span></span>  
    [Test-CsKerberosAccountAssignment](test-cskerberosaccountassignment.md)

<!-- end list -->

  - <span></span>  
    [Set-CsKerberosAccountPassword](set-cskerberosaccountpassword.md)

<!-- end list -->

  - [Test-CsWebApp](test-cswebapp.md)

  - [Test-CsWebAppAnonymous](test-cswebappanonymous.md)

</div>

<div>

## See Also


[Lync Server PowerShell Blog](http://go.microsoft.com/fwlink/p/?linkid=203150)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

