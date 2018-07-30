---
title: 'Lync Server 2013: Address Book Server cmdlets'
TOCTitle: Address Book Server cmdlets
ms:assetid: 33da45da-3c57-4d04-9679-f0e5a0cfd37e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg415643(v=OCS.15)
ms:contentKeyID: 48183793
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Address Book Server cmdlets in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-06-26_

Address Book servers are intermediaries between Active Directory Domain Services and Microsoft Lync Server 2013. The Address Book server ensures that the user information stored in Lync Server 2013 is in synch with the user information stored in Active Directory. This is done by periodically synching Address Book files with information stored in the User database. In turn, Lync Server includes a number of cmdlets for managing Address Book servers.

<div>

## Address Book Server Cmdlets

You cannot configure the Address Book Server settings in Lync Server Control Panel. Windows PowerShell is the primary tool for managing these settings. The following is a list of cmdlets that relate directly to managing the Address Book Server:

**Address Book Server**

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

