---
title: Import-Module error in Skype for Business Online caused by incorrect version of Windows PowerShell
TOCTitle: Import-Module error caused by incorrect version of Windows PowerShell
ms:assetid: 6c209f41-2b97-4dda-b0b7-e5b582d3e6b6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362802(v=OCS.15)
ms:contentKeyID: 56558819
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Import-Module error in Skype for Business Online caused by incorrect version of Windows PowerShell

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-05_

The Skype for Business Online Connector module can be run only under Windows PowerShell 3.0. If you try to import the module under a previous version of Windows PowerShell, the import process will fail with an error message similar to this:

    Import-Module : The version of the loaded PowerShell is '2.0'. The module 'D:\Program Files\Common Files\Microsoft Lync Server 2013\Modules\LyncOnlineConnector\LyncOnlineConnector.psd1' requires a minimum PowerShell version of '3.0' to execute. Please verify the installation of the PowerShell and try again.

The only way to fix this problem is to install Windows PowerShell 3.0, which is available from the Microsoft Downloads Center at <http://www.microsoft.com/en-us/download/details.aspx?id=29939>.

<div>

## See Also


[Diagnosing and resolving connection problems with Skype for Business Online](diagnosing-and-resolving-connection-problems-with-skype-for-business-online.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

