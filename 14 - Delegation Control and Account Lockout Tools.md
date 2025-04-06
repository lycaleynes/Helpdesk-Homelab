# Delegation Control and Account Lockout Tools

## Overview

This lab focuses on two key tools for Windows Server environments: **Delegation Control** in Active Directory and the **Account Lockout Status** utility. These tools help IT administrators manage user permissions and troubleshoot login issues efficiently.

## Objectives

- Understand and configure Delegation Control in Active Directory
- Create limited-permission users (e.g., password reset only)
- Use Account Lockout Status tool to diagnose login problems
- Identify sources of account lockouts (e.g., cached credentials, mobile devices)

## Part 1: Delegation Control in Active Directory

### Scenario

A contractor named **Scott** needs limited access to Active Directory to assist with password resets only. You'll create a user account for Scott and delegate password reset permissions to him.

### Steps

- Open **Active Directory Users and Computers**
- Create a new user:
   - Right-click on `Users` > `New` > `User`
     <p align="center"><img src="https://i.imgur.com/Jj7JzZD.png" height="80%" width="80%" alt="Homelab"/></p>
   - Name: `Scott`
     <p align="center"><img src="https://i.imgur.com/Fjc0BVH.png" height="80%" width="80%" alt="Homelab"/></p>
   - Password: `Welcome1` (ensure "User must change password" is unchecked)
     <p align="center"><img src="https://i.imgur.com/9HMiDcz.png" height="80%" width="80%" alt="Homelab"/></p>
- Create an Organizational Unit (OU):
   - Right-click domain root > `New` > `Organizational Unit`
     <p align="center"><img src="https://i.imgur.com/pcnc4Ly.png" height="80%" width="80%" alt="Homelab"/></p>
   - Name: `Consultants`
     <p align="center"><img src="https://i.imgur.com/hZH8Obf.png" height="80%" width="80%" alt="Homelab"/></p>
   - Move Scott to the `Consultants` OU
     <p align="center"><img src="https://i.imgur.com/c1lfZT2.png" height="80%" width="80%" alt="Homelab"/></p>
- Delegate control:
   - Right-click `Consultants` OU > `Delegate Control`
     <p align="center"><img src="https://i.imgur.com/YFfC1BW.png" height="80%" width="80%" alt="Homelab"/></p>
   - Add user `Scott`
     <p align="center"><img src="https://i.imgur.com/YvMcLDs.png" height="80%" width="80%" alt="Homelab"/></p>
     <p align="center"><img src="https://i.imgur.com/4uxoOKG.png" height="80%" width="80%" alt="Homelab"/></p>
     <p align="center"><img src="https://i.imgur.com/WMUs5JK.png" height="80%" width="80%" alt="Homelab"/></p>
   - Choose `Reset user passwords and force password change at next logon`
     <p align="center"><img src="https://i.imgur.com/ctgVvyg.png" height="80%" width="80%" alt="Homelab"/></p>
   - Finish the wizard
     <p align="center"><img src="https://i.imgur.com/VmuhJDJ.png" height="80%" width="80%" alt="Homelab"/></p>

### Result

When Scott logs into the domain and opens Active Directory Users and Computers:
- He can see users in the OU
- He can only reset passwords
- All other actions are restricted
  <p align="center"><img src="https://i.imgur.com/LbKmsuJ.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/xS9ap2m.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/s5ip8LY.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/wgU1A8g.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/GSiWnKC.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/uMNl6O8.png" height="80%" width="80%" alt="Homelab"/></p>

## Part 2: Account Lockout Status Tool

<p align="center"><img src="https://i.imgur.com/zTvYNhS.png" height="80%" width="80%" alt="Homelab"/></p>

### Why It's Important

This tool helps IT staff troubleshoot locked accounts by showing:
- Whether a user is locked out
- How many failed login attempts
- Which domain controller processed the lockout
- When the lockout occurred

### Steps

- Download **Account Lockout Status** from Microsoft's website
  <p align="center"><img src="https://i.imgur.com/93QdSeo.png" height="80%" width="80%" alt="Homelab"/></p>
- Extract and run `LockoutStatus.exe`
  <p align="center"><img src="https://i.imgur.com/2diXptN.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/rQer4zN.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/MERew5P.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/hZn3Gyx.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/xuiKAam.png" height="80%" width="80%" alt="Homelab"/></p>
- Click `File` > `Select Target`
  <p align="center"><img src="https://i.imgur.com/51Obx02.png" height="80%" width="80%" alt="Homelab"/></p>
- Enter username (e.g., `Scott`) and domain, then click OK
  <p align="center"><img src="https://i.imgur.com/XvoVXU7.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/u7nNjfN.png" height="80%" width="80%" alt="Homelab"/></p>

### Example Output

- **Status**: Locked
- **Bad Password Count**: 4
- **Last Bad Password Time**: `4/4/2025 6:21:32 AM`
- **Lockout Time**: `4/4/2025 6:21:32 AM`
- **Originating DC**: `SERVER2016.lycatech.com`
  <p align="center"><img src="https://i.imgur.com/4U0TPBT.png" height="80%" width="80%" alt="Homelab"/></p>

### Unlocking Scott's Account

- Go to **Active Directory Users and Computers** > **Consultants** > Right-click **Scott** > **Account** > Check **Unlock Account** > **OK**
  <p align="center"><img src="https://i.imgur.com/NdxwfhP.png" height="80%" width="80%" alt="Homelab"/></p>
- Log in to Scott's account
  <p align="center"><img src="https://i.imgur.com/zSxdTGf.png" height="80%" width="80%" alt="Homelab"/></p>

### Real-World Troubleshooting

- Helps identify if a user is being locked out by another device (e.g., mobile phone or secondary computer with old credentials)
- Use this before resetting a user's password to understand the root cause
- Especially useful when dealing with repeated lockouts due to cached credentials

> 🛠 If allowed in your environment, use this tool to reduce ticket resolution time and avoid unnecessary password resets.
