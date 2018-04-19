---
title: 'Lync Server 2013: Infrastructure and deployment cmdlets'
TOCTitle: Infrastructure and deployment cmdlets
ms:assetid: 0a6e872a-9f70-4f23-a4a5-8820dbf55370
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398153(v=OCS.15)
ms:contentKeyID: 48183364
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Infrastructure and deployment cmdlets in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-09_

The infrastructure and deployment cmdlets included in Microsoft Lync Server 2013 can be useful in the initial setup and deployment of the product; after Lync Server has been deployed these cmdlets can then be used to do such things as verify that components are working as expected; manage replication settings; and backup and restore the Lync Server topology, policies, and configuration settings.

<div>

## Infrastructure and Deployment Cmdlets

Administrators will rarely need to directly call many of the infrastructure and deployment. That is because these cmdlets are automatically invoked when you run Setup or the Topology Builder. (One major exception might be the **Export-CsConfiguration** cmdlet, which enables you to make a backup copy of your Lync Server topology, policies, and configuration settings.) However, and when needed, the infrastructure and deployment cmdlets can also be run from the Lync Server Management Shell or from within a script; using a script enables you to automate certain tasks. The following is a list of cmdlets that relate directly to infrastructure and deployment:

**[Active Directory cmdlets in Lync Server 2013](lync-server-2013-active-directory-cmdlets.md)**

  - <span></span>  
    [Disable-CsAdDomain](disable-csaddomain.md)

  - <span></span>  
    [Enable-CsAdDomain](enable-csaddomain.md)

  - <span></span>  
    [Get-CsAdDomain](get-csaddomain.md)

<!-- end list -->

  - <span></span>  
    [Disable-CsAdForest](disable-csadforest.md)

  - <span></span>  
    [Enable-CsAdForest](enable-csadforest.md)

  - <span></span>  
    [Get-CsAdForest](get-csadforest.md)

<!-- end list -->

  - <span></span>  
    [Get-CsAdServerSchema](get-csadserverschema.md)

  - <span></span>  
    [Install-CsAdServerSchema](install-csadserverschema.md)

**[Replication cmdlets in Lync Server 2013](lync-server-2013-replication-cmdlets.md)**

  - <span></span>  
    [Debug-CsInterPoolReplication](debug-csinterpoolreplication.md)

<!-- end list -->

  - <span></span>  
    [Invoke-CsManagementStoreReplication](invoke-csmanagementstorereplication.md)

<!-- end list -->

  - <span></span>  
    [Get-CsManagementStoreReplicationStatus](get-csmanagementstorereplicationstatus.md)

<!-- end list -->

  - <span></span>  
    [Enable-CsReplica](enable-csreplica.md)

  - <span></span>  
    [Test-CsReplica](test-csreplica.md)

<!-- end list -->

  - <span></span>  
    [Get-CsUserReplicatorConfiguration](get-csuserreplicatorconfiguration.md)

  - <span></span>  
    [New-CsUserReplicatorConfiguration](new-csuserreplicatorconfiguration.md)

  - <span></span>  
    [Remove-CsUserReplicatorConfiguration](remove-csuserreplicatorconfiguration.md)

  - <span></span>  
    [Set-CsUserReplicatorConfiguration](set-csuserreplicatorconfiguration.md)

**[Topology cmdlets jn Lync Server 2013](lync-server-2013-topology-cmdlets.md)**

  - <span></span>  
    [Get-CsPool](get-cspool.md)

<!-- end list -->

  - <span></span>  
    [Get-CsSite](get-cssite.md)

  - <span></span>  
    [Set-CsSite](set-cssite.md)

<!-- end list -->

  - <span></span>  
    [Enable-CsTopology](enable-cstopology.md)

  - <span></span>  
    [Get-CsTopology](get-cstopology.md)

  - <span></span>  
    [Publish-CsTopology](publish-cstopology.md)

  - <span></span>  
    [Test-CsTopology](test-cstopology.md)

<!-- end list -->

  - <span></span>  
    [Export-CsConfiguration](export-csconfiguration.md)

  - <span></span>  
    [Import-CsConfiguration](import-csconfiguration.md)

<!-- end list -->

  - <span></span>  
    [Get-CsServerVersion](get-csserverversion.md)

<!-- end list -->

  - <span></span>  
    [Disable-CsComputer](disable-cscomputer.md)

  - <span></span>  
    [Enable-CsComputer](enable-cscomputer.md)

  - <span></span>  
    [Get-CsComputer](get-cscomputer.md)

  - <span></span>  
    [Test-CsComputer](test-cscomputer.md)

<!-- end list -->

  - <span></span>  
    [Get-CsNetworkInterface](get-csnetworkinterface.md)

**[Backup and high availability cmdlets in Lync Server 2013](lync-server-2013-backup-and-high-availability-cmdlets.md)**

  - [Get-CsBackupServiceConfiguration](get-csbackupserviceconfiguration.md)

  - [Remove-CsBackupServiceConfiguration](remove-csbackupserviceconfiguration.md)

  - [Set-CsBackupServiceConfiguration](set-csbackupserviceconfiguration.md)

<!-- end list -->

  - [Get-CsBackupServiceStatus](get-csbackupservicestatus.md)

<!-- end list -->

  - [Invoke-CsBackupServiceSync](invoke-csbackupservicesync.md)

<!-- end list -->

  - [Debug-CsIntraPoolReplication](debug-csintrapoolreplication.md)

<!-- end list -->

  - [Backup-CsPool](backup-cspool.md)

<!-- end list -->

  - [Get-CsPoolBackupRelationship](get-cspoolbackuprelationship.md)

<!-- end list -->

  - [Get-CsPoolFabricState](get-cspoolfabricstate.md)

<!-- end list -->

  - [Invoke-CsPoolFailBack](invoke-cspoolfailback.md)

<!-- end list -->

  - [Invoke-CsPoolFailOver](invoke-cspoolfailover.md)

<!-- end list -->

  - [Get-CsPoolUpgradeReadinessState](get-cspoolupgradereadinessstate.md)

<!-- end list -->

  - [Invoke-CsStorageServiceFlush](invoke-csstorageserviceflush.md)

<!-- end list -->

  - [Sync-CsUserData](sync-csuserdata.md)

<!-- end list -->

  - [Remove-CsUserStoreBackupData](remove-csuserstorebackupdata.md)

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

