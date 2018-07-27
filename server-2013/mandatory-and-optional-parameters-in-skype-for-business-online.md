---
title: Mandatory and optional parameters in Skype for Business Online
TOCTitle: Mandatory and optional parameters
ms:assetid: e766362f-e2e9-4598-a595-fdf5eedd9ad6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362851(v=OCS.15)
ms:contentKeyID: 56558864
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Mandatory and optional parameters in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-05_

Windows PowerShell parameters fall into one of two categories: mandatory or optional. A *mandatory parameter* is a parameter that must be included when you run the command. For example, the [Remove-CsUserAcp](remove-csuseracp.md) cmdlet is used to unassign an audio conferencing provider that was previously assigned to a user. When you run **the Remove-CsUserAcp** cmdlet, you must include the Identity parameter. That parameter tells the cmdlet which user needs to have their audio conferencing provider removed. As you might expect, running this command without any parameters wouldn’t make much sense:

    Remove-CsUserAcp

In a case like this, the cmdlet would have no idea which user needs to have their audio conferencing provider removed. Instead, you must specify the Identity of the user:

    Remove-CsUserAcp -Identity "Ken Myer"

Typically, Windows PowerShell will prompt you if you omit a mandatory parameter when trying to run a command. For example, you might type the following and then press ENTER:

    Remove-CsUserAcp

If you do this, Windows PowerShell will not run this incomplete command. Instead, it will prompt you for the missing mandatory parameter:

    cmdlet Remove-CsUserAcp at command pipeline position 1
    Supply values for the following parameters:
    Identity:

If you enter a valid Identity parameter and press ENTER, Windows PowerShell will run the **Remove-CsUserAcp** cmdlet and remove the audio conferencing provider. If you change your mind and decide not to run the command after all, press Ctrl-C to terminate the command.

This is not a foolproof system, and Windows PowerShell will not always be able to prompt you for the required set of parameters. For example, some cmdlets are constructed so that either parameter A or parameter B (but not both) are mandatory. Windows PowerShell might prompt you for both parameter A and B; however, your command will then fail because you cannot use parameter A and parameter B in the same command. Because of cases like this, it’s best to include all the required parameters before you run the command, and not rely on Windows PowerShell to prompt you for the needed information.

Note, too, that formatting the parameter value can sometimes be a less-than-intuitive process. For example, when including a parameter value that contains a blank space, you’ll need to enclose that value in double quotation marks:

    -Identity "Ken Myer"

However, using quotation marks is necessary only when you type in the parameter and parameter value as part of the command to be executed. If you try to run the **Remove-CsUserAcp** cmdlet, but inadvertently leave off the Identity parameter, Windows PowerShell will then prompt you for the user Identity:

    cmdlet Remove-CsUserAcp at command pipeline position 1
    Supply values for the following parameters:
    Identity:

Then you type Ken Myer, with the Identity parameter enclosed in double quotation marks:

    cmdlet Remove-CsUserAcp at command pipeline position 1
    Supply values for the following parameters:
    Identity: "Ken Myer"

If you do this, the command will fail, with the following error message:

    Remove-CsUserAcp : Management object not found for identity ""Ken Myer"".

In this case, searched for a user with the identity "Ken Myer", with the double quotation marks included as part of the Identity parameter. If you are prompted to enter a parameter value, do not include the double quotation marks:

    cmdlet Remove-CsUserAcp at command pipeline position 1
    Supply values for the following parameters:
    Identity: Ken Myer

By comparison, an *optional parameter* is exactly what the name implies: the parameter does not need to be entered in order for the cmdlet to run. For example, the Remove-CsUserAcp has an optional parameter Name. If the Name parameter is included in the command, then only the specified audio conferencing provider will be removed. This command remove the audio conference provider with the name Fabrikam ACP but does not remove any other audio conferencing providers assigned to Ken Myer:

    Remove-CsUserAcp -Identity "Ken Myer" -Name "Fabrikam ACP"

If you leave off this optional parameter the command will still run. In that case, however, Remove-CsUserAcp will delete all the audio conferencing providers assigned to Ken Myer:

    Remove-CsUserAcp -Identity "Ken Myer"

<div>

## See Also


[An introduction to Windows PowerShell and Skype for Business Online](an-introduction-to-windows-powershell-and-skype-for-business-online.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

