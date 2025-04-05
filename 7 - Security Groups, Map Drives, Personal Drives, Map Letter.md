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
  
- Right-click **Shares** > **New Share** > Choose **Quick**
- Create the following folders:
  - `HR`
  - `Personal`
- Path: `\\Server2016\HR` and `\\Server2016\Personal`

---

## Create Security Groups

- Open **Active Directory Users and Computers**
- Navigate to the `Users` container
- Create two new security groups:
  - `HR`
  - `Personal`
- Optionally, assign a manager under the **Managed By** tab for access approval

---

## Add User to Security Groups

- Add user `Patty` to both `HR` and `Personal` security groups
- Confirm by opening `Patty`'s properties > **Member Of** tab

---

## Set Folder Permissions

### For `HR` Folder:

- Right-click `HR` share > **Properties** > **Sharing** > **Advanced Sharing**
- Click **Permissions** > Remove `Everyone`
- Add:
  - `HR` group > allow **Read** and **Change**
  - `HelpDesk` > full control (optional)

### For `Personal` Folder:

- Repeat steps above
- Give `Personal` group **Read/Write** access

---

## Map Drives on Client Side

### Manual Mapping for `HR` Drive:

- Log in as `Patty` on Desktop2
- Open **This PC** > Right-click > **Map Network Drive**
  - Path: `\\Server2016\HR`
  - Drive Letter: `Z:`
  - Check: **Reconnect at sign-in**

### Auto-Mapping via Active Directory for `Personal` Drive:

- In **ADUC**, open `Patty`'s properties > **Profile** tab
- Set **Home folder** to:
  - Drive: `P:`
  - Path: `\\Server2016\Personal\%username%`
- Click **Apply**
- A folder `\\Server2016\Personal\Patty` is automatically created
- Upon next login, the `P:` drive is mapped for Patty

---

## Recap

- Created `HR` and `Personal` shares
- Created and assigned users to security groups
- Applied NTFS and share permissions
- Mapped drives manually and via Active Directory profile

---

## What’s Next

- Dive deeper into Group Policy drive mapping
- Set up access-based enumeration (ABE)
- Automate drive mapping with scripts or GPO

---

**Tip:** Add this to your resume under "Skills":

> Configured AD-integrated shared folder permissions and user-based drive mapping

---

Stay tuned for Lab 8, where we cover advanced Group Policy Object (GPO) drive mapping and user restrictions.

