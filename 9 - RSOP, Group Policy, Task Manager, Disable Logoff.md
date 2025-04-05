# RSOP, Group Policy, Task Manager, Disable Logoff

## Overview

This lab introduces Group Policy usage in a Windows Server 2016 domain environment. We demonstrate how to create and enforce Group Policy Objects (GPOs) that apply to users in specific organizational units (OUs). Our focus is on restricting access to Task Manager and password settings using a GPO linked to the HR OU containing user `Patty` on `Desktop2`.

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
- Right-click domain root > **New GPO** > Name: `TaskManager`
- Right-click the new GPO > **Edit**

### Configure User Restrictions

- Navigate to: 
  `User Configuration > Policies > Administrative Templates > System > Ctrl+Alt+Del Options`
- Set **Remove Task Manager** to **Enabled**
- Set **Remove Change Password** to **Enabled**

### Link GPO to OU

- In Group Policy Management, drag `TaskManager` GPO onto the **HR** OU
- Right-click on it > **Enforced**

### Add User to Apply GPO

- In the **Delegation** tab of the GPO, click **Advanced**
- Add user `Patty` with **Read** permission (no edit/apply needed due to OU inheritance)

---

## Apply and Verify GPO

### On Desktop2 (Patty):

- Open **CMD**
- Run: `gpupdate /force`
- Task Manager and Change Password should now be unavailable
  - `Ctrl + Alt + Del` no longer shows the password option
  - `taskmgr` command returns a blocked message

### Verify via Command Line:

- Run: `gpresult /r`
- Confirm that `TaskManager` policy is listed under **Applied Group Policy Objects**

---

## Admin Bypass Verification

- Open CMD as `HelpDesk` with admin credentials
- Run: `taskmgr`
- Task Manager should open normally for admin

---

## View Group Policy Report

### Method 1: Group Policy Results Wizard

- On `Server2016`, open **Group Policy Management**
- Right-click **Group Policy Results** > **Wizard** > Target: `Desktop2`, user: `Patty`
- Review effective policies in the resulting report

### Method 2: Active Directory Users and Computers

- Right-click on user `Patty` > **All Tasks** > **Resultant Set of Policy (RSOP)**
- Select target computer: `Desktop2`
- Generate policy report

---

## Summary

- Created and applied a Group Policy Object to restrict Task Manager and password changes
- Linked and enforced GPO on the HR OU containing `Patty`
- Used `gpupdate`, `gpresult`, and RSOP to validate effective policy

---

## What’s Next

- Continue learning GPO by customizing Start Menu, File Explorer, and desktop icons
- Explore deploying software and printers through GPO
- Review GPO filtering and WMI filters for targeted policy applications

---

**Tip:** Add this to your resume under "Skills":

> Configured and enforced domain-level Group Policies to restrict Task Manager, password settings, and access controls using Active Directory and Windows Server Group Policy Management.

