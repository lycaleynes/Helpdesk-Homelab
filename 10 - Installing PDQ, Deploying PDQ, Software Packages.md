# Installing PDQ, Deploying PDQ, Software Packages

## Overview

This lab introduces PDQ Deploy for software deployment within a Windows Server 2016 domain environment. You will learn how to silently install applications on remote client computers using deployment packages. The scenario focuses on installing Mozilla Firefox silently to `Server 2016` from the domain controller.

## Objectives

- Understand the purpose and function of PDQ Deploy
- Prepare a domain environment for software deployment
- Create and deploy a PDQ package to a remote domain-joined computer
- Validate silent installation success

## Why Software Deployment Matters

In IT support (Tier 2 and higher), deploying software silently is critical:

- Avoids interrupting the end user
- Supports remote and VPN users
- Reduces reliance on screen-sharing tools like TeamViewer or Bomgar

Tool used include free tool like PDQ Deploy.

## Setup and Preparation

### Step 1: Install Guest Additions in VirtualBox

- Open `Server2016` VM
- Mount **Guest Additions CD Image** from the VirtualBox menu
  <p align="center"><img src="https://i.imgur.com/Qez0gcU.png" height="80%" width="80%" alt="Homelab"/></p>
- Double-click **CD Drive (D:) VirtualBox Guest**
  <p align="center"><img src="https://i.imgur.com/zW6pReF.png" height="80%" width="80%" alt="Homelab"/></p>
- Double-click **VBoxWindowsAdditions**
  <p align="center"><img src="https://i.imgur.com/WdU8Ps7.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Next**
  <p align="center"><img src="https://i.imgur.com/kDn1SAz.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/XT4FZLa.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Install**
  <p align="center"><img src="https://i.imgur.com/ueEseQp.png" height="80%" width="80%" alt="Homelab"/></p>
- Wait for install to finish
  <p align="center"><img src="https://i.imgur.com/r4sMVbF.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Reboot now** > **Finish**
  <p align="center"><img src="https://i.imgur.com/BsoF8XG.png" height="80%" width="80%" alt="Homelab"/></p>

This enables file sharing between host and VM.

### Step 2: Create Shared Folder for Software Packages

- Right-click on the folder on the bottom right of VirtualBox > Click **Shared Folders Settings**
  <p align="center"><img src="https://i.imgur.com/6PlZLVZ.png" height="80%" width="80%" alt="Homelab"/></p>
- Choose Folder Path > **Downloads** > `lycatechlab` > **OK**
  <p align="center"><img src="https://i.imgur.com/mUEIbLb.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/10an144.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/McWvlAv.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/els4zi9.png" height="80%" width="80%" alt="Homelab"/></p>
- Now, you can see the folder on Server 2016
  <p align="center"><img src="https://i.imgur.com/0ZZ6SBZ.png" height="80%" width="80%" alt="Homelab"/></p>
- Remove Disk from Virtual Drive
  <p align="center"><img src="https://i.imgur.com/WfUQkrc.png" height="80%" width="80%" alt="Homelab"/></p>

### Step 3: Move PDQ Installer to Shared Folder

- Download PDQ Deploy Free version from the official website
  <p align="center"><img src="https://i.imgur.com/lblUlrZ.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/clViczI.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/ZL4CnL8.png" height="80%" width="80%" alt="Homelab"/></p>
- Place installer in `lycatech lab` shared folder
  <p align="center"><img src="https://i.imgur.com/SVsyo92.png" height="80%" width="80%" alt="Homelab"/></p>
- In Server2016, copy it to the Desktop
  <p align="center"><img src="https://i.imgur.com/DaUutkE.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/ajmHNkV.png" height="80%" width="80%" alt="Homelab"/></p>

### Step 4: Set Server to Use Dynamic IP (Temporarily)

- Go to **Network Settings** in VirtualBox > Set Attached to: **Bridge Adapter**
  <p align="center"><img src="https://i.imgur.com/0LDkQBY.png" height="80%" width="80%" alt="Homelab"/></p>
- Go to **Network Connections > Properties > IPv4 Settings**
- Change to **Obtain IP address automatically**
  <p align="center"><img src="https://i.imgur.com/QhNfq00.png" height="80%" width="80%" alt="Homelab"/></p>
- Confirm internet access using `ping 8.8.8.8`
  <p align="center"><img src="https://i.imgur.com/vRRhfnY.png" height="80%" width="80%" alt="Homelab"/></p>

### Step 5: Install .NET Framework 4.8

- Required for PDQ Deploy installation
- Run the PDQ Deploy installer
  <p align="center"><img src="https://i.imgur.com/oNwxLLh.png" height="80%" width="80%" alt="Homelab"/></p>
- Installer will prompt if missing
  <p align="center"><img src="https://i.imgur.com/b1oEPij.png" height="80%" width="80%" alt="Homelab"/></p>
- Accept terms and install the application
  <p align="center"><img src="https://i.imgur.com/RRoZwoC.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/bYBwnp3.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Yes**
  <p align="center"><img src="https://i.imgur.com/pjOQuuE.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Finish**
  <p align="center"><img src="https://i.imgur.com/a4Ud7uf.png" height="80%" width="80%" alt="Homelab"/></p>

## PDQ Deploy Installation

- Run the PDQ Deploy installer
  <p align="center"><img src="https://i.imgur.com/3rSndyf.png" height="80%" width="80%" alt="Homelab"/></p>
- Accept terms > **Next** > **Install**
  <p align="center"><img src="https://i.imgur.com/GJTIhN8.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/RFGWZng.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/qRcsHAT.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/ClB28pZ.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Finish**
  <p align="center"><img src="https://i.imgur.com/rnbDCH6.png" height="80%" width="80%" alt="Homelab"/></p>
- Launch PDQ Deploy
  <p align="center"><img src="https://i.imgur.com/rnbDCH6.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Next**
  <p align="center"><img src="https://i.imgur.com/qNErSFl.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Enter license key**
  <p align="center"><img src="https://i.imgur.com/qNErSFl.png" height="80%" width="80%" alt="Homelab"/></p>
- Copy license key from the website 
  <p align="center"><img src="https://i.imgur.com/dWaMihO.png" height="80%" width="80%" alt="Homelab"/></p>
- Enter the license key and email
  <p align="center"><img src="https://i.imgur.com/JrSC0Hb.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Next**
  <p align="center"><img src="https://i.imgur.com/BhmVueM.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/ZOd2j4K.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Finish** > **Continue**
  <p align="center"><img src="https://i.imgur.com/djOfC1n.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/1vzy6Tu.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/pJQvtin.png" height="80%" width="80%" alt="Homelab"/></p>

> Note: This is a trial version with limited access to some packages

## Deploying Software with PDQ

### Step 1: Create a Deployment

- Go to **Package Library** > Search for **Firefox** > Download Selected
  <p align="center"><img src="https://i.imgur.com/RJYViRv.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Packages** > Right-click **Mozilla Firefox** > Click **Deploy Once**
  <p align="center"><img src="https://i.imgur.com/90oLczf.png" height="80%" width="80%" alt="Homelab"/></p>
- Choose **Targets > Active Directory > Computers**
  <p align="center"><img src="https://i.imgur.com/zt4p8fW.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/6KQe300.png" height="80%" width="80%" alt="Homelab"/></p>
- Select `SERVER2016` > Click OK > Deploy Now
  <p align="center"><img src="https://i.imgur.com/LL7PDTG.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/Q7i1G6D.png" height="80%" width="80%" alt="Homelab"/></p>

### Step 2: Confirm Deployment

- Monitor PDQ interface for status: *Success*
  <p align="center"><img src="https://i.imgur.com/9r829ev.png" height="80%" width="80%" alt="Homelab"/></p>
- On `Server 2016`, verify Firefox is installed
  <p align="center"><img src="https://i.imgur.com/Wu0C6rq.png" height="80%" width="80%" alt="Homelab"/></p>
  
## Post-Installation

### Reset Static IP Address

- Return IPv4 settings to:
  - IP: `10.1.10.2`
  - Subnet: `255.0.0.0`
  - Gateway: `10.1.10.1`
  - DNS: `10.1.10.2`
  - Alt DNS: `10.1.10.1`
    <p align="center"><img src="https://i.imgur.com/akCZgAU.png" height="80%" width="80%" alt="Homelab"/></p>
- Return Network Settings to:
  - Host-only Adapter
    <p align="center"><img src="https://i.imgur.com/YBYTOgy.png" height="80%" width="80%" alt="Homelab"/></p>
