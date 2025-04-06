# PDQ Inventory, Hardware Inventory, Applications

## Overview

This lab demonstrates how to deploy software and perform inventory scans using PDQ Deploy and PDQ Inventory in a Windows Server 2016 domain environment. PDQ tools allow IT support staff to silently install applications, monitor installed software, and gather system hardware and configuration information.

## Objectives

- Install PDQ Deploy and PDQ Inventory on the domain controller
- Share files across VirtualBox using Guest Additions
- Deploy applications silently using PDQ Deploy
- View detailed system inventory using PDQ Inventory
- Understand use cases for software inventory and remote tools in enterprise IT

## Install PDQ Deploy and Inventory

### Install PDQ Inventory:

- Navigate to shared folder: `C:\lycatech lab`
  <p align="center"><img src="https://i.imgur.com/ueSJ7ye.png" height="80%" width="80%" alt="Homelab"/></p>
- Launch `PDQInventorySetup.exe`
  <p align="center"><img src="https://i.imgur.com/1Gx9Bzr.png" height="80%" width="80%" alt="Homelab"/></p>
- Follow the installer steps
  <p align="center"><img src="https://i.imgur.com/ptef5HD.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/p9djl28.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/m9Q3pPq.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/YUWssZk.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/neJPGAK.png" height="80%" width="80%" alt="Homelab"/></p>
- Open **PDQ Inventory** from the Start menu
  <p align="center"><img src="https://i.imgur.com/nHUE1Sr.png" height="80%" width="80%" alt="Homelab"/></p>

### Install PDQ Deploy (if not already installed):

- Also available from the shared folder
- Run `PDQDeploySetup.exe`
- Follow the installer steps

## Using PDQ Inventory

### Key Features:

- **Computer Overview**:
  - Current user, OS, IP, MAC, hostname, domain
  - RAM, CPU, disk space, architecture (x64/x86)
  - Installed applications

- **Useful Tabs**:
  - **Applications**: Lists installed programs
  - **CPU/Memory/NIC**: Shows hardware details
  - **Hotfixes**: Installed Windows Updates
  - **Printers**: Installed printers
  - **Shares**: Shared folders (e.g., `C$`, `Admin$`)
  - **Processes/Services**: Live status and control

- **Remote Access**:
  - Remote into computers using **RDP** or **Remote Assistant**
  - Access C$ or Admin$ shares directly
  - Run remote commands and PowerShell
  - Manage MMC snap-ins remotely

- **Generate Reports**:
  - Right-click a device > **Run Report** > Choose a report type (e.g., Applications, Devices)
    <p align="center"><img src="https://i.imgur.com/GLHLzrP.png" height="80%" width="80%" alt="Homelab"/></p>
  - Export as **CSV** or print to **PDF** for documentation
    <p align="center"><img src="https://i.imgur.com/66wMmCG.png" height="80%" width="80%" alt="Homelab"/></p>

## Using PDQ Deploy

### Basic Deployment Steps:

- In PDQ Deploy, click **New Package** or select a prebuilt package (e.g., Mozilla Firefox)
   <p align="center"><img src="https://i.imgur.com/GuTwXfS.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Deploy Once**
   <p align="center"><img src="https://i.imgur.com/PjpJdgj.png" height="80%" width="80%" alt="Homelab"/></p>
- Choose targets:
   - **Choose Targets > Active Directory > Computers > Desktop2**
     <p align="center"><img src="https://i.imgur.com/Alf1rgS.png" height="80%" width="80%" alt="Homelab"/></p>
     <p align="center"><img src="https://i.imgur.com/BbBIaUv.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Deploy Now**
   <p align="center"><img src="https://i.imgur.com/5jn5kTH.png" height="80%" width="80%" alt="Homelab"/></p>
- Monitor status in real-time (e.g., success or failure)
   <p align="center"><img src="https://i.imgur.com/O5A3TF1.png" height="80%" width="80%" alt="Homelab"/></p>
   <p align="center"><img src="https://i.imgur.com/Lget9eU.png" height="80%" width="80%" alt="Homelab"/></p>

### Example Use Case:

- User reports Mozilla Firefox is not installed
- Admin uses PDQ Inventory to confirm Mozilla Firefox is missing
- Admin deploys Mozilla Firefox silently via PDQ Deploy
- User receives Mozilla Firefox without interruption

## Use Cases in Enterprise IT

- **Inventory Reports**:
  - Export lists of computers missing applications or updates
  - Report on memory, disk, OS versions for all devices

- **Compliance and Auditing**:
  - Validate if systems meet patch levels or have required software

- **Software Deployment**:
  - Deploy applications silently across multiple endpoints

- **Remote Troubleshooting**:
  - Access file shares and registry remotely
  - Restart systems or run CMD/PowerShell
