# Printer Set Up On Server 2016, NTFS, Printer Cloud

## Overview

This lab covers how to install, configure, and manage printers using Windows Server 2016. You will learn how to add printers through Print Management, control access via Active Directory groups, and understand how centralized print solutions like Print Cloud can simplify printer management in enterprise environments.

## Objectives

- Install the Print and Document Services role
- Add and configure a local printer
- Share and publish a printer in Active Directory
- Assign printer permissions via security groups
- Understand centralized print solutions like Print Cloud

## Installing Print Services Role

- On **Server2016**, open **Server Manager**
- Navigate to: **Manage > Add Roles and Features**
  <p align="center"><img src="https://i.imgur.com/8yTY2B1.png" height="80%" width="80%" alt="Homelab"/></p>
- Select: **Print and Document Services** > Add features
- Install only the **Print Server** option
- Complete the wizard and close when finished
  <p align="center"><img src="https://i.imgur.com/ugqCtlQ.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/r4P3usc.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/WOb6usN.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/sI5fVj5.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/33UrGOa.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/xy9Hlx5.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/fUPaXq1.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/HnzR5CT.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/j5eCfMi.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/diBtTuC.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/JAVkgZl.png" height="80%" width="80%" alt="Homelab"/></p>

## Configuring Printer via Print Management

- Open **Tools > Print Management**
  <p align="center"><img src="https://i.imgur.com/BHYVvxM.png" height="80%" width="80%" alt="Homelab"/></p>
- Expand **Print Servers > Server2016 > Printers**
  <p align="center"><img src="https://i.imgur.com/nmFCt86.png" height="80%" width="80%" alt="Homelab"/></p>
- Right-click **Printers** > **Add Printer**
  <p align="center"><img src="https://i.imgur.com/QuJjWZr.png" height="80%" width="80%" alt="Homelab"/></p>
- Choose: **Add a new printer using an existing port or new port**
  <p align="center"><img src="https://i.imgur.com/hDhxPlf.png" height="80%" width="80%" alt="Homelab"/></p>
- Choose: **Install a new driver**
  <p align="center"><img src="https://i.imgur.com/loGQvbw.png" height="80%" width="80%" alt="Homelab"/></p>
- Choose a manufacturer/model or provide a driver
  <p align="center"><img src="https://i.imgur.com/HQWyL0P.png" height="80%" width="80%" alt="Homelab"/></p>
- Complete the wizard
  <p align="center"><img src="https://i.imgur.com/ZuhBmMM.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/ZBRWuVp.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/2CqbU0E.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/tSehQfj.png" height="80%" width="80%" alt="Homelab"/></p>

## Sharing and Publishing the Printer

- Right-click the new printer > **Properties**
  <p align="center"><img src="https://i.imgur.com/zMI0PXF.png" height="80%" width="80%" alt="Homelab"/></p>
- Under **Sharing**, check:
   - Share this printer
   - List in the directory (for AD discovery)
     <p align="center"><img src="https://i.imgur.com/SUvi9z6.png" height="80%" width="80%" alt="Homelab"/></p>
- Apply and confirm

## Configuring Printer Security

- In printer **Properties > Security**:
   - Remove `Everyone` group
   - Add a specific AD security group (e.g., `HR`)
   - Grant necessary permissions (Print, Manage Documents)
     <p align="center"><img src="https://i.imgur.com/p2JDOHE.png" height="80%" width="80%" alt="Homelab"/></p>
     <p align="center"><img src="https://i.imgur.com/4Jfbul9.png" height="80%" width="80%" alt="Homelab"/></p>
     <p align="center"><img src="https://i.imgur.com/CnPy9lY.png" height="80%" width="80%" alt="Homelab"/></p>
     <p align="center"><img src="https://i.imgur.com/l7NlrMp.png" height="80%" width="80%" alt="Homelab"/></p>
     <p align="center"><img src="https://i.imgur.com/3XoSYgp.png" height="80%" width="80%" alt="Homelab"/></p>
     <p align="center"><img src="https://i.imgur.com/AhIqYp2.png" height="80%" width="80%" alt="Homelab"/></p>
     <p align="center"><img src="https://i.imgur.com/Xzn9ric.png" height="80%" width="80%" alt="Homelab"/></p>
     <p align="center"><img src="https://i.imgur.com/AVOi1zw.png" height="80%" width="80%" alt="Homelab"/></p>
- Confirm group members can now access the printer
  <p align="center"><img src="https://i.imgur.com/EpqxHlR.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/RkA1Fip.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/zQlVzgz.png" height="80%" width="80%" alt="Homelab"/></p>

## User-Side Printer Discovery

- On **Desktop2** (Jason’s machine):
   - Open **Control Panel > Devices and Printers**
     <p align="center"><img src="https://i.imgur.com/pVF8WEP.png" height="80%" width="80%" alt="Homelab"/></p>
   - Use **Add a printer** > **Find a printer in the directory**
     <p align="center"><img src="https://i.imgur.com/ppGMBe7.png" height="80%" width="80%" alt="Homelab"/></p>
   - The shared printer should appear (e.g., `\\Server2016\HPPrinter01`)
     <p align="center"><img src="https://i.imgur.com/NfThiPR.png" height="80%" width="80%" alt="Homelab"/></p>
- Select and install the printer
  <p align="center"><img src="https://i.imgur.com/0lW3zZR.png" height="80%" width="80%" alt="Homelab"/></p>
- Confirm it appears in **Devices and Printers**
  <p align="center"><img src="https://i.imgur.com/Nl1mHL3.png" height="80%" width="80%" alt="Homelab"/></p>

## Printer Visibility Based on Permissions

- Only users added via AD security group (e.g., `HR`) can discover or install the printer
- Users not part of the group will not see the printer
- Important in sensitive departments (HR, Legal, Compliance) to ensure print job confidentiality
