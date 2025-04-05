# Join Win 10 PC To Domain, Group Policy, CMD, RSOP Report

## Description

In this lab, we're adding a second Windows 10 virtual machine to our domain lab environment. We already have `Server 2016` running with Active Directory and one client machine `Desktop1` acting as a help desk computer. Now we're going to create `Desktop2` to simulate a user workstation. We'll also create an organizational unit (OU), assign a user to it, apply policies, and verify attributes and password expiration via GUI and CMD.

## What You Need

- VirtualBox
- Windows Server 2016 (already set up)
- Existing domain: `lycatech.com`
- Windows 10 ISO
- Previously created help desk account and RSAT tools

## Steps

### Set Up the Second Windows 10 VM

- Open VirtualBox  
- Create new VM named `Desktop-2` > Check **SKip Unattended Installation**
  <p align="center"><img src="https://i.imgur.com/JFSwmgf.png" height="80%" width="80%" alt="Homelab"/></p>
- Select Windows 10 and assign 8 GB RAM
  <p align="center"><img src="https://i.imgur.com/JFSwmgf.png" height="80%" width="80%" alt="Homelab"/></p>
- Choose **Create a Virtual Hard Disk Now** > Finish
  <p align="center"><img src="https://i.imgur.com/tl1YIkG.png" height="80%" width="80%" alt="Homelab"/></p>
- Choose **Windows 10 Pro**, not Home (so it can join a domain)  
- Create a local account (e.g., `Administrator`) and skip setting up online account  

### Configure the Local Administrator

- After install, enable the local `Administrator` account  
- Set the password to something consistent (e.g., `Welcome1`)  
- Delete any extra user accounts created during install  

### Assign a Static IP Address

- Open **Control Panel > Network and Sharing Center > Change adapter settings**  
- Set static IP:  
  - IP: `10.1.10.4`  
  - Subnet: `255.255.255.0`  
  - Gateway: `10.1.10.1`  
  - DNS: `10.1.10.2`  
- Change **Network Adapter** in VirtualBox to **Host-Only Adapter**  
- Test connectivity by pinging `kevtech.com`  

### Rename the Computer and Join Domain

- Rename the computer to `DESKTOP2`  
- Restart the machine  
- Go to system properties > change settings > domain: `kevtech.com`  
- Authenticate with the domain credentials (e.g., help desk account)  
- Restart again  

### Create a New User and Organizational Unit

- Open **Active Directory Users and Computers**  
- Right-click domain root > New > Organizational Unit > name it `HR`  
- Create a new user (e.g., `Paddy`) and place in `HR` OU  
- Set password to `Welcome1`  

### Move Existing Help Desk Account to IT OU

- Create another OU called `IT`  
- Move `HelpDesk` user into `IT` OU  

### Enable Advanced Features and View Attribute Editor

- In **Active Directory Users and Computers**, go to **View > Advanced Features**  
- Go to `HR` OU > double-click `Paddy`  
- Click **Attribute Editor** tab  
- Scroll down to view:  
  - `lastLogon`  
  - `pwdLastSet`  
  - `accountExpires`  

### Use CMD to Check Account Info

- On any domain-joined machine with RSAT:  
  - Open CMD as admin  
  - Run: `net user Paddy /domain`  
  - Verify password expiration, last set date, and group membership  

### Configure Group Policy Settings

- Open **Group Policy Management**  
- Right-click domain > Edit default domain policy  
- Navigate to **Computer Configuration > Windows Settings > Security Settings > Account Policies**  
  - Set **Maximum password age** to `90 days`  
  - Set **Account lockout threshold** to `5 attempts`  
  - Apply changes  

### Force and Verify Group Policy

- Right-click domain > **Group Policy Update** (forces policy refresh)  
- Open **Group Policy Management** > Settings tab  
- Confirm updated policy values appear under **Password Policy** and **Account Lockout Policy**  

### Log In as User on Desktop2

- On Desktop2, login as user `Paddy` using password `Welcome1`  
- Open CMD and run `net user Paddy /domain` to check policy enforcement  
- Open **Active Directory Users and Computers** > double-click `Paddy` > Attribute Editor  
  - Confirm last login value has updated  
