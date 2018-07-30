---
title: Automatically connecting to Skype for Business Online whenever you start Windows PowerShell
TOCTitle: Automatically connecting to Skype for Business Online whenever you start Windows PowerShell
ms:assetid: 68f76c36-5dd6-48ea-b19a-d65593199e4c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362799(v=OCS.15)
ms:contentKeyID: 56558816
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Automatically connecting to Skype for Business Online whenever you start Windows PowerShell

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-05_

If you can’t remember all the commands required to connect to Skype for Business Online, you can configure things so that all you need to do is double-click a shortcut file, enter your Skype for Business Online password, and, just like that, be connected to Skype for Business Online.

To do this, start by opening Notepad (or any other text editor) and then paste in the following commands, substituting your Skype for Business Online account name for kenmyer@litwareinc.com:

    $credential = Get-Credential "kenmyer@litwareinc.com"
    $session = New-CsOnlineSession -Credential $credential 
    Import-PSSession $session

Save the file with a .PS1 file extension (for example, C:\\Scripts\\LyncOnline.ps1).

After you have saved the file, complete the following procedure to create a desktop shortcut that launches Windows PowerShell and runs the script on startup:

1.  Right-click the desktop, click **New**, and then click **Shortcut**.

2.  In the **Create Shortcut** wizard, type the following in the **Type the location of the item** box and then click **Next** (remember to use the path to the script file that you just created):
    
        powershell.exe -noexit C:\Scripts\LyncOnline.ps1

3.  In the **Type a name for this shortcut** box, type a name for the shortcut (for example, **Skype for Business Online**), and then click **Finish**.

4.  The next time you want to use Windows PowerShell to manage Skype for Business Online, just double-click the new shortcut and enter your password. The script will take care of making the connection and setting up the new remote session.

This new session typically will not get stored in the variable $session. Instead it will usually be given the session ID 1. This will not affect your session in any way, at least not until it comes time to close down the session. To do that, you’ll need to reference the session ID when calling the **Remove-PSSession** cmdlet:

    Remove-PSSession 1

You can verify the ID given to your Skype for Business Online session by running this command from the Windows PowerShell prompt:

    Get-PSSession

<div>

## See Also


[Configuring your computer for Skype for Business Online management](configuring-your-computer-for-skype-for-business-online-management.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

