# Active Directory Account Creation, CMD Commands

## Description

This lab is part three of a hands-on training series designed for individuals entering IT support roles, especially in help desk and desktop support. In this phase, we built on the existing Windows Server 2016 domain environment by:

  - Creating a custom Help Desk user account
  - Demonstrating advanced user management features in Active Directory
  - Reviewing essential CMD commands for IT support roles

## Lab Environment

  - Platform: Oracle VirtualBox
  - Server OS: Windows Server 2016
  - Domain: lycatech.com
  - Tools Used:
    - Active Directory Users and Computers (ADUC)
    - Active Directory Administrative Center
    - Windows Command Prompt (CMD)

## Open Active Directory Management Tools
- Open **Server Manager**
- Click **Tools** in the top-right menu
- Select **Active Directory Users and Computers**
  <p align="center"><img src="https://i.imgur.com/keS5uYD.png" height="80%" width="80%" alt="Homelab"/></p>

## Explore the Domain Structure in ADUC
- Expand the domain node: `lycatech.com`
- View the following containers:
  - Builtin
  - Computers
  - Domain Controllers
  - Users
- Go to **View > Advanced Features** to show extra tabs and system containers
  <p align="center"><img src="https://i.imgur.com/dZ91Ck8.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/mHoq0sT.png" height="80%" width="80%" alt="Homelab"/></p>

## Create a New User Manually
- Right-click the **Users** container > **New > User**
  <p align="center"><img src="https://i.imgur.com/Kn0Zxob.png" height="80%" width="80%" alt="Homelab"/></p>
- Enter:
  - First name
  - Last name
  - User logon name (e.g., `jdoe@lycatech.com`)
    <p align="center"><img src="https://i.imgur.com/LWS1mL1.png" height="80%" width="80%" alt="Homelab"/></p>

## Search for an Existing User (Guest)
- Right-click the **Users** container > **Find**
  <p align="center"><img src="https://i.imgur.com/TmwTySb.png" height="80%" width="80%" alt="Homelab"/></p>
- Enter "guest" in the name field
  <p align="center"><img src="https://i.imgur.com/OXYbJCr.png" height="80%" width="80%" alt="Homelab"/></p>
- Change the **In:** dropdown to **Entire Directory**
  <p align="center"><img src="https://i.imgur.com/vIZkBXm.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Find Now**
  <p align="center"><img src="https://i.imgur.com/Vis5qEj.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/6XpFOiG.png" height="80%" width="80%" alt="Homelab"/></p>
- Double-click or right-click > **Properties**
  <p align="center"><img src="https://i.imgur.com/k0PkHqy.png" height="80%" width="80%" alt="Homelab"/></p>
- Review:
  - **General** tab
    <p align="center"><img src="https://i.imgur.com/q98DMfX.png" height="80%" width="80%" alt="Homelab"/></p>
  - **Object** tab:
    - Canonical name: `lycatech.com/Users/Guest`
    - Created/Modified dates
      <p align="center"><img src="https://i.imgur.com/0f3tuTM.png" height="80%" width="80%" alt="Homelab"/></p>

## Enable Active Directory Recycle Bin
- Open **Active Directory Administrative Center** via Start Menu
  <p align="center"><img src="https://i.imgur.com/ZeYWiQj.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **lycatech (local)** in the left pane
  <p align="center"><img src="https://i.imgur.com/HMwZvbZ.png" height="80%" width="80%" alt="Homelab"/></p>
- In the **Tasks** pane, click **Enable Recycle Bin**
  <p align="center"><img src="https://i.imgur.com/fYt46BT.png" height="80%" width="80%" alt="Homelab"/></p>
- Confirm the action by clicking **OK**
  <p align="center"><img src="https://i.imgur.com/uch0sTi.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/eTvT1Ee.png" height="80%" width="80%" alt="Homelab"/></p>
- Click the **Refresh** icon
  <p align="center"><img src="https://i.imgur.com/1Jft4Ms.png" height="80%" width="80%" alt="Homelab"/></p>
- Confirm **Deleted Objects** container appears
  <p align="center"><img src="https://i.imgur.com/0iEe2bi.png" height="80%" width="80%" alt="Homelab"/></p>

## Copy Administrator to Create Helpdesk
- Right-click **Administrator** > **Copy**
  <p align="center"><img src="https://i.imgur.com/9YqVVAz.png" height="80%" width="80%" alt="Homelab"/></p>
- Enter:
  - First name: helpdesk
  - User logon name: `helpdesk@lycatech.com`
- Click **Next**
  <p align="center"><img src="https://i.imgur.com/Kbpuk0L.png" height="80%" width="80%" alt="Homelab"/></p>
- Set password
- Check:
  - Password never expires
  - Account is disabled (uncheck)
- Click **Next** > **Finish**
  <p align="center"><img src="https://i.imgur.com/6mTXWyd.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/3fxFY3L.png" height="80%" width="80%" alt="Homelab"/></p>
- Right-click **helpdesk** > **Properties**
- Compare **Member Of** tab with **Administrator**:
  - Administrators
  - Domain Admins
  - Domain Users
  - Enterprise Admins
  - Group Policy Creator Owners
  - Schema Admins
    <p align="center"><img src="https://i.imgur.com/LlqVfM2.png" height="80%" width="80%" alt="Homelab"/></p>

## Verify Using Command Prompt
- Open **Command Prompt** (search `cmd`)
  <p align="center"><img src="https://i.imgur.com/MQR6zeM.png" height="80%" width="80%" alt="Homelab"/></p>
- Run `ipconfig` and `ipconfig /all`:
  - Verify IP address, subnet, gateway, DNS suffix
    <p align="center"><img src="https://i.imgur.com/7Hak8y7.png" height="80%" width="80%" alt="Homelab"/></p>
    <p align="center"><img src="https://i.imgur.com/SHu6x0U.png" height="80%" width="80%" alt="Homelab"/></p>
- Run `net use`:
  - Confirm no mapped drives
    <p align="center"><img src="https://i.imgur.com/NFfqL8c.png" height="80%" width="80%" alt="Homelab"/></p>
- Run `net user helpdesk /domain`:
  - Confirm:
    - Account active: Yes
    - Password never expires: Yes
    - Group memberships match admin
      <p align="center"><img src="https://i.imgur.com/IP5Ak5o.png" height="80%" width="80%" alt="Homelab"/></p>
