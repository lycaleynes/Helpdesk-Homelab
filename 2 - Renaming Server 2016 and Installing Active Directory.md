# Renaming Server 2016 and Installing Active Directory

## Description

This project is part two of a multi-part series designed for aspiring IT professionals preparing for entry-level roles in help desk or IT support. The focus of this phase is installing and configuring Active Directory Domain Services (AD DS) on a Windows Server 2016 virtual machine using VirtualBox.

This part of the lab simulates setting up a domain controller, renaming the server, and launching Active Directory tools—key tasks for any junior system administrator or support tech.

## Lab Environment

  - Platform: Oracle VirtualBox
  - Operating System: Windows Server 2016 (evaluation ISO)
  - Host Requirements:
    - Virtualization-enabled BIOS
    - Minimum 4 GB RAM and 50 GB disk space recommended
    - VirtualBox Extension Pack installed
  - Domain Name: ``lycatech.com`` (custom static, non-internet-facing domain for lab use)

## Renaming the Server

  - Enter the password on the login screen.
    <p align="center"><img src="https://i.imgur.com/rBUrdTL.png" height="80%" width="80%" alt="Homelab"/></p>
  - Right-click This PC > Properties.
    <p align="center"><img src="https://i.imgur.com/h3TWz7Q.png" height="80%" width="80%" alt="Homelab"/></p>
  - Click Change settings next to the computer name.
    <p align="center"><img src="https://i.imgur.com/T0dmD5O.png" height="80%" width="80%" alt="Homelab"/></p>
  - Click Change > Set computer name to ``Server2016``.
    <p align="center"><img src="https://i.imgur.com/6kmAgO3.png" height="80%" width="80%" alt="Homelab"/></p>
  - Confirm and restart the system to apply the new name.
    <p align="center"><img src="https://i.imgur.com/QpcPTM1.png" height="80%" width="80%" alt="Homelab"/></p>
    <p align="center"><img src="https://i.imgur.com/S3co5nJ.png" height="80%" width="80%" alt="Homelab"/></p>
    <p align="center"><img src="https://i.imgur.com/dHPiqck.png" height="80%" width="80%" alt="Homelab"/></p>

## System Performance Optimization

  - Right-click This PC > Properties.
    <p align="center"><img src="https://i.imgur.com/h3TWz7Q.png" height="80%" width="80%" alt="Homelab"/></p>
  - Click Advanced system settings.
    <p align="center"><img src="https://i.imgur.com/Ug6MoHE.png" height="80%" width="80%" alt="Homelab"/></p>
  - Click Settings under Performance.
    <p align="center"><img src="https://i.imgur.com/1DBvohr.png" height="80%" width="80%" alt="Homelab"/></p>
  - Select Adjust for best performance.
  - Click Apply.
    <p align="center"><img src="https://i.imgur.com/d3PO0PP.png" height="80%" width="80%" alt="Homelab"/></p>

## Add AD DS Role

  - Launch Server Manager.
    <p align="center"><img src="https://i.imgur.com/fMtZw1j.png" height="80%" width="80%" alt="Homelab"/></p>
  - Click Manage > Add Roles and Features.
    <p align="center"><img src="https://i.imgur.com/Ae369F4.png" height="80%" width="80%" alt="Homelab"/></p>
  - Proceed through:
    - Before You Begin
      <p align="center"><img src="https://i.imgur.com/wzzHasI.png" height="80%" width="80%" alt="Homelab"/></p>
    - Installation Type → Select Role-based or feature-based
      <p align="center"><img src="https://i.imgur.com/KnIYJoK.png" height="80%" width="80%" alt="Homelab"/></p>
    - Server Selection → Choose your current server
      <p align="center"><img src="https://i.imgur.com/w7Dx9es.png" height="80%" width="80%" alt="Homelab"/></p>
    - Server Roles → Check Active Directory Domain Services
      <p align="center"><img src="https://i.imgur.com/vqDom2M.png" height="80%" width="80%" alt="Homelab"/></p>
  - In the popup, click Add Features.
    <p align="center"><img src="https://i.imgur.com/YBWyETo.png" height="80%" width="80%" alt="Homelab"/></p>
  - Click Next through:
    - Features
      <p align="center"><img src="https://i.imgur.com/3VWkb3m.png" height="80%" width="80%" alt="Homelab"/></p>
    - AD DS Overview
      <p align="center"><img src="https://i.imgur.com/xeA07gF.png" height="80%" width="80%" alt="Homelab"/></p>
  - Confirm selections and click Install.
    <p align="center"><img src="https://i.imgur.com/nQ60BIq.png" height="80%" width="80%" alt="Homelab"/></p>
  - Wait for installation to finish.
    <p align="center"><img src="https://i.imgur.com/x0bkDy4.png" height="80%" width="80%" alt="Homelab"/></p>

## Promote Server to Domain Controller

  - Click Promote this server to a domain controller.
    <p align="center"><img src="https://i.imgur.com/BG6VAA4.png" height="80%" width="80%" alt="Homelab"/></p>
  - Choose Add a new forest → Enter root domain name: ``lycatech.com``
    <p align="center"><img src="https://i.imgur.com/h15dSvC.png" height="80%" width="80%" alt="Homelab"/></p>
  - Set Domain Controller Options:
    - DNS and Global Catalog selected
    - Set DSRM password
      <p align="center"><img src="https://i.imgur.com/cYWQsWO.png" height="80%" width="80%" alt="Homelab"/></p>
  - Ignore DNS delegation warning → Click Next
    <p align="center"><img src="https://i.imgur.com/pMrmeO6.png" height="80%" width="80%" alt="Homelab"/></p>
  - Confirm NetBIOS name: LYCATECH
    <p align="center"><img src="https://i.imgur.com/GvBwaNQ.png" height="80%" width="80%" alt="Homelab"/></p>
  - Use default NTDS & SYSVOL paths
    <p align="center"><img src="https://i.imgur.com/tLhSM82.png" height="80%" width="80%" alt="Homelab"/></p>
  - Review configuration.
    <p align="center"><img src="https://i.imgur.com/dIudV2k.png" height="80%" width="80%" alt="Homelab"/></p>
  - Wait for Prerequisites Check → All checks passed
    <p align="center"><img src="https://i.imgur.com/iPvThy1.png" height="80%" width="80%" alt="Homelab"/></p>
  - Click Install.
    <p align="center"><img src="https://i.imgur.com/qCt8VHd.png" height="80%" width="80%" alt="Homelab"/></p>
  - Wait for installation to finish.
    <p align="center"><img src="https://i.imgur.com/9WnxXEW.png" height="80%" width="80%" alt="Homelab"/></p>

## Post-Install & Reboot

  - System signs out and restarts
    <p align="center"><img src="https://i.imgur.com/YeJ4ShM.png" height="80%" width="80%" alt="Homelab"/></p>
  - System applies computer settings
    <p align="center"><img src="https://i.imgur.com/lzSnQp3.png" height="80%" width="80%" alt="Homelab"/></p>
  - Press Ctrl+Alt+Del to log in
    <p align="center"><img src="https://i.imgur.com/Q8fV83f.png" height="80%" width="80%" alt="Homelab"/></p>
  - Log in as ``LYCATECH\Administrator``
    <p align="center"><img src="https://i.imgur.com/xhlo7bK.png" height="80%" width="80%" alt="Homelab"/></p>

## Verify AD DS Installation

  - Open Server Manager > Tools > Active Directory Users and Computers
    <p align="center"><img src="https://i.imgur.com/keS5uYD.png" height="80%" width="80%" alt="Homelab"/></p>
  - Right click Active Directory Users and Computers > Pin to taskbar.
    <p align="center"><img src="https://i.imgur.com/XvAXwqg.png" height="80%" width="80%" alt="Homelab"/></p>
  - Verify domain lycatech.com is listed
  - Active Directory is fully initialized
    <p align="center"><img src="https://i.imgur.com/BAS300L.png" height="80%" width="80%" alt="Homelab"/></p>
