---
title: Firewall policies for Windows PCs | Microsoft Intune
ms.custom: na
ms.reviewer: na
ms.service: microsoft-intune
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid:
author: robstackmsft
---
# Help protect Windows PCs using Windows Firewall policies in Microsoft Intune
Microsoft Intune can help you to secure Windows PCs you manage with the Intune client in a number of ways, including the use of policies that allow you to configure Windows Firewall settings on PCs.

If you have not yet installed the Intune Windows PC client on your computers, see [Install the Windows PC client with Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Use the information in the following sections to help you configure, deploy and monitor Windows Firewall policies on Windows PCs.

## Use Intune policies to manage the Windows Firewall
The Windows Firewall policy lets you create and deploy settings that control the Windows Firewall on managed PCs. You cannot manage custom exceptions for Windows Firewall and these settings do not affect third-party firewalls.

> [!NOTE]
> If Microsoft Intune policy and Group Policy are configured to manage the same setting on the PC, the Group Policy setting overrides the Microsoft Intune policy. For information about how to avoid conflicts between Intune policies and Group Policy, see [Resolve GPO and Microsoft Intune policy conflicts](resolve-gpo-and-microsoft-intune-policy-conflicts.md).
>
> If you want to deploy Windows Firewall settings to computers running Windows Vista, you must first install [Hotfix KB971800](http://support2.microsoft.com/kb/971800) on these computers.

> [!IMPORTANT]
> To manage the Windows Firewall using Intune, you must ensure that the following two services are enabled on the computers you will manage:
>
> -   Windows Firewall
> -   IPsec Policy Agent

## Configure a Windows Firewall policy

1.  In the [Microsoft Intune administration console](https://manage.microsoft.com/), choose **Policy** &gt; **Add Policy**.

2.  Configure and deploy a **Windows Firewall Settings** policy. You can use recommended settings or customize the settings. If you need more information about how to create and deploy policies, see [Common Windows PC management tasks with the Microsoft Intune computer client](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

    The tables after this procedure show the values you can configure in the policy and also the recommended values that will be used if you don’t customize the policy.

You can view the deployed Windows Firewall policy on the **All Policies** page of the **Policy** workspace.

## Policy settings for Windows Firewall

### Turn on Windows Firewall

|Setting name|Details|
|------------------|--------------------|
|**Domain profile**|Enables the Windows Firewall on managed computers while they are connected to domain networks, for example while at the workplace.<br /><br />Recommended value: **Yes**|
|**Private profile**|Enables the Windows Firewall on managed computers while they are connected to trusted networks, for example while on a home network.<br /><br />Recommended value: **Yes**|
|**Public profile**|Enables the Windows Firewall on managed computers while they are connected to untrusted networks in public places, for example while at a coffee shop.<br /><br />Recommended value: **Yes**<br /><br />Required operating system: Windows Vista or later versions|

### Block all incoming connections, including those in the list of allowed programs
> [!IMPORTANT]
> If your environment includes managed computers that are running Windows Vista with no service packs installed, you must either install the update associated with [article 971800](http://go.microsoft.com/fwlink/?LinkId=188405) in the Microsoft Knowledge Base or else disable the **Block all incoming connections** policy settings in policies deployed to those computers.

|Setting name|Details|
|------------------|--------------------|
|**Domain profile**|Blocks all incoming connections while the computers are connected to domain networks, such as at a workplace. This includes those connections in the list of exceptions.<br /><br />Recommended value: **No**|
|**Private profile**|Blocks all incoming connections while the computers are connected to trusted networks, such as a home network. This includes those connections in the list of exceptions.<br /><br />Recommended value: **No**|
|**Public profile**|Blocks all incoming connections while the computers are connected to untrusted networks at public places, such as at a coffee shop. This includes those connections in the list of exceptions.<br /><br />Recommended value: **No**<br /><br />Required operating system: Windows Vista or later versions|

### Notify the user when Windows Firewall blocks a new program

|Setting name|Details|
|------------------|--------------------|
|**Domain profile**|Notifies users when Windows Firewall blocks a new program while the computers are connected to domain networks, such as at a workplace.<br /><br />Recommended value: **Yes**|
|**Private profile**|Notifies users when Windows Firewall blocks a new program while the computers are connected to trusted networks, such as a home network.<br /><br />Recommended value: **Yes**|
|**Public profile**|Notifies users when Windows Firewall blocks a new program while the computers are connected to untrusted networks at public places, such as a coffee shop.<br /><br />Recommended value: **Yes**<br /><br />Required operating system: Windows Vista or later versions|

### Predefined Exceptions

|Setting name|Details|
|------------------|--------------------|
|**BranchCache - Content Retrieval**|If enabled, lets BranchCache clients use HTTP to retrieve content from one another in the distributed mode and from the hosted cache in hosted cache mode. This setting uses HTTP.<br /><br />Recommended value: Not configured<br /><br />(Windows 7 or later).|
|**BranchCache - Hosted Cache Client**|If enabled, lets BranchCache clients use a hosted cache. This setting uses HTTPS.<br /><br />Recommended value: Not configured<br /><br />(Windows 7 or later).|
|**BranchCache - Hosted Cache Server**|If enabled, lets BranchCache clients can use a hosted cache to communicate with other clients. This setting uses HTTPS.<br /><br />Recommend value: Not configured<br /><br />(Windows 7 or later).|
|**BranchCache - Peer Discovery**|If enabled, lets BranchCache clients use the WS Discovery protocol to look up content availability on the local subnet.<br /><br />Recommended value: Not configured<br /><br />(Windows 7 or later).|
|**BITS Peercaching**|If enabled, lets clients use Background Intelligent Transfer Service (BITS) to find and share files that are stored in the BITS cache on clients in the same subnet. This setting uses WSDAPI and RPC.<br /><br />Recommended value: Not configured<br /><br />(Windows Vista or later).|
|**Connect to a Network Projector**|If enabled, lets users connect to projectors over wired or wireless networks to project presentations. This setting uses WSDAPI.<br /><br />Recommended value: Not configured<br /><br />(Windows Vista or later).|
|**Core Networking**|If enabled, lets clients use IPv4 and IPv6 to connect to network resources.<br /><br />Recommended value: Not configured<br /><br />(Windows Vista or later).|
|**Distributed Transaction Coordinator**|If enabled, allows managed computers to coordinate transactions that update transaction-protected resources, like databases, message queues, and file systems.<br /><br />Recommended value: Not configured<br /><br />(Windows Vista or later).|
|**File and Printer Sharing**|If enabled, allows users to share local files and printers with other users on the network. This setting uses NetBIOS, LLMNR, SMB, and RPC.<br /><br />Recommended value: Not configured<br /><br />(Windows XP or later).|
|**HomeGroup**|If enabled, allow managed computers to participate in a HomeGroup network.<br /><br />Recommended value: Not configured<br /><br />(Windows 7 or later).|
|**iSCSI Service**|If enabled, allows managed computers to connect to iSCSI servers and devices.<br /><br />Recommended value: Not configured<br /><br />(Windows Vista or later).|
|**Key Management Service**|If enabled, lets computers be counted for license compliance in enterprise environments.<br /><br />Recommended value: Not configured<br /><br />(Windows Vista or later).|
|**Media Center Extenders**|If enabled, allows Media Center Extenders to communicate with computers that are running Windows Media Center. This setting uses SSDP and qWave.<br /><br />Recommended value: Not configured<br /><br />(Windows Vista or later).|
|**Netlogon Service**|If enabled, configures a security channel between domain clients and a domain controller for authenticating users and services. This setting uses RPC.<br /><br />Recommended value: Not configured<br /><br />(Windows Vista or later).|
|**Network Discovery**|If enabled, lets computers discover other devices and be discovered by other devices on the network. This setting uses Function Discovery Host and Publication Services and SSDP, NetBIOS, LLMNR, and UPnP network protocols.<br /><br />Recommended value: Not configured<br /><br />(Windows Vista or later).|
|**Performance Logs and Alerts**|If enabled, allows the Performance Logs and Alerts service to be remotely managed. This setting uses RPC.<br /><br />Recommended value: Not configured<br /><br />(Windows Vista or later).|
|**Remote Administration**|If enabled, allows remote administration of the computer.<br /><br />Recommended value: Not configured<br /><br />(Windows Vista or later).|
|**Remote Assistance**|If enabled, lets users of managed computers request remote assistance from other users on the network. This setting uses SSDP, PNRP, Teredo, and UPnP network protocols.<br /><br />Recommended value: Not configured<br /><br />(Windows XP or later).|
|**Remote Desktop**|If enabled, lets the computer use Remote Desktop to access other computers.<br /><br />Recommended value: Not configured<br /><br />(Windows XP or later).|
|**Remote Event Log Management**|If enabled, let’s client event logs be viewed and managed remotely. This setting uses Named Pipes and RPC.<br /><br />Recommended value: Not configured<br /><br />(Windows Vista or later).|
|**Remote Scheduled Tasks Management**|If enabled, allows remote management of the task scheduling service. This setting uses RPC.<br /><br />Recommended value: Not configured<br /><br />(Windows Vista or later).|
|**Remote Service Management**|If enabled, allows remote management of local services on clients. This setting uses Named Pipes and RPC.<br /><br />Recommended value: Not configured<br /><br />(Windows Vista or later).|
|**Remote Volume Management**|If enabled, allows remote software and hardware disk volume management. This setting uses RPC.<br /><br />Recommended value: Not configured<br /><br />(Windows Vista or later).|
|**Routing and Remote Access**|If enabled, allows incoming VPN and remote access connections to computers.<br /><br />Recommended value: Not configured<br /><br />(Windows Vista or later).|
|**Secure Socket Tunneling Protocol**|If enabled, allows incoming VPN connections to managed computers by using Secure Socket Tunneling Protocol (SSTP). This setting uses HTTPS.<br /><br />Recommended value: Not configured<br /><br />(Windows Vista or later).|
|**SNMP Trap**|If enabled, lets managed computers receive SNMP Trap service traffic.<br /><br />Recommended value: Not configured<br /><br />(Windows Vista or later).|
|**UPnP Framework**|If enabled, configures the UPnP Framework service on computers to let them discover and use UPnP certified devices.<br /><br />Recommended value: Not configured<br /><br />(Windows XP or later).|
|**Windows Collaboration Computer Name Registration Service**|If enabled, lets computers find and communicate with other computers by using the Peer Name Resolution Protocol. This setting uses SSDP and PNRP.<br /><br />Recommended value: Not configured<br /><br />(Windows Vista or later).|
|**Windows Media Player**|If enabled, lets users receive streaming media over UDP.<br /><br />Recommended value: Not configured<br /><br />(Windows Vista or later).|
|**Windows Media Player Network Sharing Service**|If enabled, lets users share media over a network. This setting uses the SSDP, qWave, and UPnP network protocols.<br /><br />Recommended value: Not configured<br /><br />(Windows Vista or later).|
|**Windows Media Player Network Sharing Service (Internet)**|If enabled, lets users share home media over the Internet.<br /><br />Recommended value: Not configured<br /><br />(Windows 7 or later).|
|**Windows Meeting Space**|If enabled, lets users collaborate over a network to share documents, programs, or their desktop. This setting uses DFSR and P2P.<br /><br />Recommended value: Not configured<br /><br />(Windows Vista or later).|
|**Windows Peer to Peer Collaboration Foundation**|If enabled, configures various peer-to-peer programs and technologies to allow them to connect. This setting uses SSDP and PNRP.<br /><br />Recommended value: Not configured<br /><br />(Windows Vista or later).|
|**Windows Remote Management (Compatibility)**|If enabled, allows remote management of managed computers by using WS-Management, a Web services-based protocol for remote management of operating systems and devices.<br /><br />Recommended value: Not configured<br /><br />(Windows Vista or later).|
|**Windows Remote Management**|If enabled, allows remote management of managed computers by using WS-Management, a Web services-based protocol for remote management of operating systems and devices.<br /><br />Recommended value: Not configured<br /><br />(Windows 8 or later)|
|**Windows Virtual PC**|If enabled, lets virtual machines, communicate with other computers.<br /><br />Recommended value: Not configured<br /><br />(Windows 7 only)|
|**Wireless Portable Devices**|If enabled, allows the transfer of media from a network-enabled camera or media device to managed computers by using the Media Transfer Protocol (MTP). This setting uses SSDP and UPnP network protocols.<br /><br />Recommended value: Not configured<br /><br />(Windows Vista or later).|

### See also
[Policies to protect Windows PCs](policies-to-protect-windows-pcs.md)