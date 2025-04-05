# Security Groups, Map Drives, Personal Drives, Map Letter

## Overview

In this lab, we set up shared drive permissions using security groups and demonstrate two ways to map network drives. We use the user account `Patty` for testing. This is a crucial real-world skill for IT support roles and often asked about in interviews.

## Objectives

- Create shared folders on Server 2016
- Create AD security groups
- Assign users to security groups
- Set NTFS/share permissions
- Map drives manually and via Active Directory

## Create Shared Folders

- On Server 2016, open **Server Manager** > **File and Storage Services** > **Shares**
  <p align="center"><img src="https://i.imgur.com/ML2Ll4G.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/wgr8EtS.png" height="80%" width="80%" alt="Homelab"/></p>
- Right-click **Shares** > **New Share** > Choose **SMB Share - Quick**
  <p align="center"><img src="https://i.imgur.com/6uCLo2K.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/zPIpcSe.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Next**
  <p align="center"><img src="https://i.imgur.com/J9bEu2T.png" height="80%" width="80%" alt="Homelab"/></p>
- Create the following folders:
  - `HR`
  - `Personal`
- Path: `\\Server2016\HR` and `\\Server2016\Personal`
  <p align="center"><img src="https://i.imgur.com/ln54QiD.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Next**
  <p align="center"><img src="https://i.imgur.com/VqqQBwN.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/FHkBXvW.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Create**
  <p align="center"><img src="https://i.imgur.com/YkBlhqe.png" height="80%" width="80%" alt="Homelab"/></p>
- Wait for share to be completed > **Close**
  <p align="center"><img src="https://i.imgur.com/2pnLon4.png" height="80%" width="80%" alt="Homelab"/></p>

## Create Security Groups

- Open **Active Directory Users and Computers**
- Navigate to the `Users` container > Right-click > New > Group
  <p align="center"><img src="https://i.imgur.com/IKhBNNX.png" height="80%" width="80%" alt="Homelab"/></p>
- Create two new security groups:
  - `HR`
  - `Personal`
    <p align="center"><img src="https://i.imgur.com/wrML07s.png" height="80%" width="80%" alt="Homelab"/></p>
- Optionally, assign a manager under the **Managed By** tab for access approval
  <p align="center"><img src="https://i.imgur.com/b79eFt4.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/Rtm0jP2.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/2WqQXjl.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/TDp1K8u.png" height="80%" width="80%" alt="Homelab"/></p>
- Repeat steps above for `Personal`

## Add Description to Security Groups

- Go to **File Explorer** > **This PC** > **Local Disk (C:)** > **Shares** > Right-click on **Personal** > **Properties** > Copy **Network Path**
  <p align="center"><img src="https://i.imgur.com/3npcv9F.png" height="80%" width="80%" alt="Homelab"/></p>
- Go back to **Active Directory Users and Computers** > **Users** > **Personal** > Paste `\\SERVER2016\Personal (Share Folder)` to the **Description** > **OK**
  <p align="center"><img src="https://i.imgur.com/joz39Ve.png" height="80%" width="80%" alt="Homelab"/></p>
- Repeat steps above for `HR`

## Add User to Security Groups

- Add user `Jason Williams` to both `HR` and `Personal` security groups
  <p align="center"><img src="https://i.imgur.com/7ipvUv6.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/ycIoSYr.png" height="80%" width="80%" alt="Homelab"/></p>
- Confirm by opening `Jason Williams`' properties > **Member Of** tab
  <p align="center"><img src="https://i.imgur.com/cuDFdQK.png" height="80%" width="80%" alt="Homelab"/></p>

## Set Folder Permissions

### For `HR` Folder:

- Right-click `HR` share > **Properties** > **Sharing** > **Advanced Sharing**
  <p align="center"><img src="https://i.imgur.com/H116zIX.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Disable Inheritance** > **Convert inherited permissions into explicit permissions on this object**
  <p align="center"><img src="https://i.imgur.com/AzsFtzu.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/77BQyMH.png" height="80%" width="80%" alt="Homelab"/></p>
- Remove Users Accounts
  <p align="center"><img src="https://i.imgur.com/I4wCOMP.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/QQInW2Z.png" height="80%" width="80%" alt="Homelab"/></p>
- Click Add
  - `helpdesk` > full control
  - `HR` group > full control
  <p align="center"><img src="https://i.imgur.com/JdPTxCo.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/jKtWEOZ.png" height="80%" width="80%" alt="Homelab"/></p>
- Go back to properties > Sharing > Share > HR > Read/Write > Share > Done
  <p align="center"><img src="https://i.imgur.com/fsmW6KV.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/vijUD6p.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/mtuRQ8u.png" height="80%" width="80%" alt="Homelab"/></p>

### For `Personal` Folder:

- Repeat steps above
- Give `Personal` group **Read/Write** access

## Map Drives on Client Side

### Manual Mapping for `HR` Drive:

- Log in as `Jason` on Desktop2
- Open **This PC** > Right-click > **Map Network Drive**
  <p align="center"><img src="https://i.imgur.com/dA1gl3w.png" height="80%" width="80%" alt="Homelab"/></p>
  
  - Path: `\\Server2016\HR`
  - Drive Letter: `Z:`
  - Check: **Reconnect at sign-in**
    <p align="center"><img src="https://i.imgur.com/LnYS2wW.png" height="80%" width="80%" alt="Homelab"/></p>
    <p align="center"><img src="https://i.imgur.com/mKW4qhS.png" height="80%" width="80%" alt="Homelab"/></p>

### Auto-Mapping via Active Directory for `Personal` Drive:

- In **ADUC**, open `Jason`'s properties > **Profile** tab
- Set **Home folder** to:
  - Drive: `P:`
  - Path: `\\Server2016\Personal\%username%`
- Click **Apply**
  <p align="center"><img src="https://i.imgur.com/x403dp4.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/5UQDiy5.png" height="80%" width="80%" alt="Homelab"/></p>
- A folder `\\Server2016\Personal\jwilliams` is automatically created
  <p align="center"><img src="https://i.imgur.com/zy0gmRR.png" height="80%" width="80%" alt="Homelab"/></p>
- Upon next login, the `P:` drive is mapped for Patty
  <p align="center"><img src="https://i.imgur.com/o0MQ3Of.png" height="80%" width="80%" alt="Homelab"/></p>
