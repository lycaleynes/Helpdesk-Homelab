# RSOP, Group Policy, Task Manager, Disable Logoff

## Overview

This lab introduces Group Policy usage in a Windows Server 2016 domain environment. We demonstrate how to create and enforce Group Policy Objects (GPOs) that apply to users in specific organizational units (OUs). Our focus is on restricting access to Task Manager and password settings using a GPO linked to the HR OU containing user `Jason` on `Desktop2`.

## Objectives

- Understand the purpose of Group Policy in enterprise environments
- Create a GPO to restrict Task Manager and password changes
- Link and enforce a GPO to an organizational unit
- Validate GPO enforcement using CMD commands and user behavior

## Group Policy Use Case

In remote work environments, Group Policy is commonly used to restrict shutdown/restart buttons. This prevents users from powering off domain-joined machines that require remote access.

## GPO Implementation: Disable Task Manager & Password Change

### Create GPO in Group Policy Management

- On `Server2016`, open **Group Policy Management**
  <p align="center"><img src="https://i.imgur.com/6HW5uA5.png" height="80%" width="80%" alt="Homelab"/></p>
- Go to **Group Policy Objects** > **New**
  <p align="center"><img src="https://i.imgur.com/qKzRsRC.png" height="80%" width="80%" alt="Homelab"/></p>
- Name the New GPO `Task Manager` > **OK**
  <p align="center"><img src="https://i.imgur.com/TVeIlnc.png" height="80%" width="80%" alt="Homelab"/></p>

### Add User to Apply GPO

- Go to the New GPO `Task Manager` > **Delegation** > **Add** > `jwilliams` > **OK**
  <p align="center"><img src="https://i.imgur.com/EPiWCzr.png" height="80%" width="80%" alt="Homelab"/></p>
- Make `Jason` have only `Read` permissions
  <p align="center"><img src="https://i.imgur.com/KfcilBC.png" height="80%" width="80%" alt="Homelab"/></p>

### Configure User Restrictions

- Navigate to: 
  `User Configuration > Policies > Administrative Templates > System > Ctrl+Alt+Del Options`
- Set **Remove Task Manager** to **Enabled**
  <p align="center"><img src="https://i.imgur.com/EB6uM2q.png" height="80%" width="80%" alt="Homelab"/></p>
- Set **Remove Change Password** to **Enabled**
  <p align="center"><img src="https://i.imgur.com/1QJfpQF.png" height="80%" width="80%" alt="Homelab"/></p>

### Link GPO to OU

- In Group Policy Management, copy and paste `TaskManager` GPO onto the **HR** OU
  <p align="center"><img src="https://i.imgur.com/9rrCcxr.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/XY9a4Ln.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/vy0KBjR.png" height="80%" width="80%" alt="Homelab"/></p>
- Right-click on it > **Enforced**
  <p align="center"><img src="https://i.imgur.com/KApUohX.png" height="80%" width="80%" alt="Homelab"/></p>

## Apply and Verify GPO

### On Desktop2 (Jason):

- Open **CMD**
- Run: `gpupdate /force`
   <p align="center"><img src="https://i.imgur.com/mkBp2aE.png" height="80%" width="80%" alt="Homelab"/></p>
- Task Manager and Change Password should now be unavailable
  - `Ctrl + Alt + Del` no longer shows the password option
    <p align="center"><img src="https://i.imgur.com/Mg5aybe.png" height="80%" width="80%" alt="Homelab"/></p>
  - `taskmgr` command returns a blocked message
    <p align="center"><img src="https://i.imgur.com/HxxMrZZ.png" height="80%" width="80%" alt="Homelab"/></p>

### Verify via Command Line:

- Run: `gpresult /r`
- Confirm that `TaskManager` policy is listed under **Applied Group Policy Objects**
  <p align="center"><img src="https://i.imgur.com/7Zasfqn.png" height="80%" width="80%" alt="Homelab"/></p>
- Run: `taskmgr`
  <p align="center"><img src="https://i.imgur.com/lpKyxdl.png" height="80%" width="80%" alt="Homelab"/></p>

## Admin Bypass Verification

- Open CMD as `Administrator` with admin credentials
  <p align="center"><img src="https://i.imgur.com/RYYBB5P.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/0qWU94l.png" height="80%" width="80%" alt="Homelab"/></p>
- Run: `taskmgr`
- Task Manager should open normally for admin
  <p align="center"><img src="https://i.imgur.com/gcuAyuq.png" height="80%" width="80%" alt="Homelab"/></p>

**Tip:** Add this to your resume under "Skills":

> Configured and enforced domain-level Group Policies to restrict Task Manager, password settings, and access controls using Active Directory and Windows Server Group Policy Management.

