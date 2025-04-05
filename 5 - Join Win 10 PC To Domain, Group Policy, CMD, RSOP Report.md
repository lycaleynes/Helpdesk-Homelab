# Join Win 10 PC To Domain, Group Policy, CMD, RSOP Report

## Description

In this lab, we're adding a second Windows 10 virtual machine to our domain lab environment. We already have `Server 2016` running with Active Directory and one client machine `Desktop1` acting as a help desk computer. Now we're going to create `Desktop2` to simulate a user workstation. We'll also create an organizational unit (OU), assign a user to it, apply policies, and verify attributes and password expiration via GUI and CMD.

## What You Need

- VirtualBox
- Windows Server 2016 (already set up)
- Existing domain: `lycatech.com`
- Windows 10 ISO
- Previously created help desk account and RSAT tools

## Set Up the Second Windows 10 VM

- Open VirtualBox  
- Create new VM named `Desktop-2` > Check **Skip Unattended Installation**
  <p align="center"><img src="https://i.imgur.com/JFSwmgf.png" height="80%" width="80%" alt="Homelab"/></p>
- Select Windows 10 and assign 8 GB RAM
  <p align="center"><img src="https://i.imgur.com/JFSwmgf.png" height="80%" width="80%" alt="Homelab"/></p>
- Choose **Create a Virtual Hard Disk Now** > Finish
  <p align="center"><img src="https://i.imgur.com/tl1YIkG.png" height="80%" width="80%" alt="Homelab"/></p>
- Start the VM and boot from the ISO
- Click **Next**
  <p align="center"><img src="https://i.imgur.com/pxpE6cA.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Install now**
  <p align="center"><img src="https://i.imgur.com/scn0lnr.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **I don't have a product key**
  <p align="center"><img src="https://i.imgur.com/wkYDDLp.png" height="80%" width="80%" alt="Homelab"/></p>
- Install **Windows 10 Pro** (not Home)
  <p align="center"><img src="https://i.imgur.com/IORcls5.png" height="80%" width="80%" alt="Homelab"/></p>
- Accept the license terms > **Next**
  <p align="center"><img src="https://i.imgur.com/EGIDrKW.png" height="80%" width="80%" alt="Homelab"/></p>
- Choose **Custom: Install Windows only (advanced)**
  <p align="center"><img src="https://i.imgur.com/JuyqAQi.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Next**
  <p align="center"><img src="https://i.imgur.com/Bl7LFuP.png" height="80%" width="80%" alt="Homelab"/></p>
- Wait for installation to finish
  <p align="center"><img src="https://i.imgur.com/4f5gFmv.png" height="80%" width="80%" alt="Homelab"/></p>
- Choose a region
  <p align="center"><img src="https://i.imgur.com/rZo41jB.png" height="80%" width="80%" alt="Homelab"/></p>
- Choose your keyboard layout
  <p align="center"><img src="https://i.imgur.com/oLBM6uZ.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Skip**
  <p align="center"><img src="https://i.imgur.com/Dneaj8o.png" height="80%" width="80%" alt="Homelab"/></p>
- Choose **Set up for personal use** > **Next**
  <p align="center"><img src="https://i.imgur.com/JDj1tUp.png" height="80%" width="80%" alt="Homelab"/></p>
- Choose **Offline account**
  <p align="center"><img src="https://i.imgur.com/wYPEU6f.png" height="80%" width="80%" alt="Homelab"/></p>
- Choose **Limited experience**
  <p align="center"><img src="https://i.imgur.com/r5mkLiT.png" height="80%" width="80%" alt="Homelab"/></p>
- Name the user for the PC
  <p align="center"><img src="https://i.imgur.com/mLeqHf4.png" height="80%" width="80%" alt="Homelab"/></p>
- Create a password for the user
  <p align="center"><img src="https://i.imgur.com/EOBdN74.png" height="80%" width="80%" alt="Homelab"/></p>
- Confirm the password
  <p align="center"><img src="https://i.imgur.com/mqxG3gR.png" height="80%" width="80%" alt="Homelab"/></p>
- Create security questions for your account
  <p align="center"><img src="https://i.imgur.com/w49fg7A.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Accept**
  <p align="center"><img src="https://i.imgur.com/s2BVKoE.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/jGzCdra.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Skip**
  <p align="center"><img src="https://i.imgur.com/iXrNcq2.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Accept**
  <p align="center"><img src="https://i.imgur.com/5KIDVSI.png" height="80%" width="80%" alt="Homelab"/></p>
- Wait for setup to finish
  <p align="center"><img src="https://i.imgur.com/bDYFP1h.png" height="80%" width="80%" alt="Homelab"/></p>

## Create a New User and Organizational Unit in Server 2016

- Open **Active Directory Users and Computers**  
- Right-click domain root > New > Organizational Unit > name it `HR`
  <p align="center"><img src="https://i.imgur.com/kmT5jal.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/yU3Ofpn.png" height="80%" width="80%" alt="Homelab"/></p>
- Create a new user (e.g., `Jason Williams`) and place in `HR` OU
  <p align="center"><img src="https://i.imgur.com/40ZhUzd.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/HIuPgLz.png" height="80%" width="80%" alt="Homelab"/></p>
- Set password to whatever you want
  <p align="center"><img src="https://i.imgur.com/2EI0H8x.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/ZOzrg0o.png" height="80%" width="80%" alt="Homelab"/></p>
- Right-click domain root > New > Organizational Unit > name it `IT`
  <p align="center"><img src="https://i.imgur.com/RJIFf5k.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/SPvQmiQ.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/68QNzdD.png" height="80%" width="80%" alt="Homelab"/></p>
- Move `helpdesk` and place in `IT` OU
  <p align="center"><img src="https://i.imgur.com/68QNzdD.png" height="80%" width="80%" alt="Homelab"/></p>

## Use CMD to Check Account Info on Windows 10 Lab

- Open CMD as admin  
- Run: `net user jwillaims /domain`
  <p align="center"><img src="https://i.imgur.com/e238LoN.png" height="80%" width="80%" alt="Homelab"/></p>
- Verify password expiration, last set date, and group membership

## Enable Advanced Features and View Attribute Editor on Windows 10 Lab

- In **Active Directory Users and Computers** > Advanced Features**
  <p align="center"><img src="https://i.imgur.com/9jAkG82.png" height="80%" width="80%" alt="Homelab"/></p> 
- Right-click domain root > **Find**
  <p align="center"><img src="https://i.imgur.com/bDmXk6s.png" height="80%" width="80%" alt="Homelab"/></p> 
- Search for `jason` > **Find Now**
  <p align="center"><img src="https://i.imgur.com/sJZqlt6.png" height="80%" width="80%" alt="Homelab"/></p> 
- Double-click on `Jason Williams` > **Object**
  <p align="center"><img src="https://i.imgur.com/BU28QIj.png" height="80%" width="80%" alt="Homelab"/></p> 
- Double-click on `Jason Williams` > **Object**
  <p align="center"><img src="https://i.imgur.com/BU28QIj.png" height="80%" width="80%" alt="Homelab"/></p> 
  <p align="center"><img src="https://i.imgur.com/dGQ5789.png" height="80%" width="80%" alt="Homelab"/></p>
- Go to `HR` OU > double-click `Jason Williams`
  <p align="center"><img src="https://i.imgur.com/RdPaN60.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Attribute Editor** tab
  <p align="center"><img src="https://i.imgur.com/V79PvEX.png" height="80%" width="80%" alt="Homelab"/></p>
- Scroll down to view:  
  - `lastLogon`  
  - `pwdLastSet`  
  - `accountExpires`
 
## Generating RSOP Report using Windows 10 Lab

- In **Active Directory Users and Computers**, go to `IT` OU > Right-click `helpdesk` > **All tasks** > **Resultant Set of Policy (Logging)**
  <p align="center"><img src="https://i.imgur.com/p6MAOMl.png" height="80%" width="80%" alt="Homelab"/></p>
- Choose **This computer** > **Next**
  <p align="center"><img src="https://i.imgur.com/xTBdX5R.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Next**
  <p align="center"><img src="https://i.imgur.com/9m0VDt1.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/dYmdnSh.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Finish**
  <p align="center"><img src="https://i.imgur.com/7PO2UoH.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/FWmoWW4.png" height="80%" width="80%" alt="Homelab"/></p>

## Configure Group Policy Settings

- In **Server Manager**, open **Group Policy Management**
  <p align="center"><img src="https://i.imgur.com/yVaVRvP.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/5eVMTbO.png" height="80%" width="80%" alt="Homelab"/></p>
- Right-click **Default Domain** > **Edit**
  <p align="center"><img src="https://i.imgur.com/9KVslaa.png" height="80%" width="80%" alt="Homelab"/></p>
- Navigate to **Computer Configuration > Windows Settings > Security Settings > Account Policies**
  <p align="center"><img src="https://i.imgur.com/VQjSNkH.png" height="80%" width="80%" alt="Homelab"/></p>
  
  - Double-click **Account Lockout Policy**
    <p align="center"><img src="https://i.imgur.com/6Vln5vh.png" height="80%" width="80%" alt="Homelab"/></p>
  - Double-click **Account lockout duration**
    <p align="center"><img src="https://i.imgur.com/1JknSBr.png" height="80%" width="80%" alt="Homelab"/></p>
  - Check **Define this policy setting** > Set **Account lockout duration** to `30 minutes` > **OK**
    <p align="center"><img src="https://i.imgur.com/1nGUvUG.png" height="80%" width="80%" alt="Homelab"/></p>
    <p align="center"><img src="https://i.imgur.com/GJ3bNa7.png" height="80%" width="80%" alt="Homelab"/></p>
    
  - Check **Define this policy setting** > Set **Account lockout threshold** to `4 attempts` > **OK**
    <p align="center"><img src="https://i.imgur.com/FMxfy1U.png" height="80%" width="80%" alt="Homelab"/></p>
  - Go to **Password Policy** > Check **Define this policy setting** > Set **Maximum password age** to `90 days` > **OK**
    <p align="center"><img src="https://i.imgur.com/rxlLw5l.png" height="80%" width="80%" alt="Homelab"/></p>
- Verify that policy was placed
  <p align="center"><img src="https://i.imgur.com/GlEPazR.png" height="80%" width="80%" alt="Homelab"/></p>

## Rename the Computer on Desktop 2

- Go to **File Explorer** > Right-click **This PC** > **Properties**
  <p align="center"><img src="https://i.imgur.com/cKrSQOY.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Rename this PC (advanced)**
  <p align="center"><img src="https://i.imgur.com/H3Dmzsv.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Change**
  <p align="center"><img src="https://i.imgur.com/gZn7ptJ.png" height="80%" width="80%" alt="Homelab"/></p>
- Change name to `Desktop2` > **OK**
  <p align="center"><img src="https://i.imgur.com/TU0cP7Q.png" height="80%" width="80%" alt="Homelab"/></p>
- Restart the machine
  <p align="center"><img src="https://i.imgur.com/qplCEpu.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/eF9hsc4.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/agh3iQY.png" height="80%" width="80%" alt="Homelab"/></p>

### Enable the Local Administrator on Desktop 2

- Go to **File Explorer** > Right-click **This PC** > **Manage**
  <p align="center"><img src="https://i.imgur.com/ZHrxYZh.png" height="80%" width="80%" alt="Homelab"/></p>
- Go to **Local Users and Groups** > **Users**
  <p align="center"><img src="https://i.imgur.com/R30nFZK.png" height="80%" width="80%" alt="Homelab"/></p>
- Right click on **Administrator** > **Properties**
  <p align="center"><img src="https://i.imgur.com/LMys9bD.png" height="80%" width="80%" alt="Homelab"/></p>
- Uncheck **Account is disabled** > **Apply** > **OK**
  <p align="center"><img src="https://i.imgur.com/E0Ye9jA.png" height="80%" width="80%" alt="Homelab"/></p>
- Right click on **Administrator** > **Set Password** > **Proceed**
  <p align="center"><img src="https://i.imgur.com/TuZjSu3.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/q8Mhwnp.png" height="80%" width="80%" alt="Homelab"/></p>
- Set a password for your Administrator account > **OK**
  <p align="center"><img src="https://i.imgur.com/dSDW0rY.png" height="80%" width="80%" alt="Homelab"/></p>
- Sign out from the User account
  <p align="center"><img src="https://i.imgur.com/ynMFVvO.png" height="80%" width="80%" alt="Homelab"/></p>
- Sign in to your Administrator account
  <p align="center"><img src="https://i.imgur.com/TeT857c.png" height="80%" width="80%" alt="Homelab"/></p>

## Delete User Profile

- Right-click **This PC** > **Properties** > **Advanced system settings**
  <p align="center"><img src="https://i.imgur.com/XfnGjHx.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/tO4eART.png" height="80%" width="80%" alt="Homelab"/></p>
- Under **User Profiles** > **Settings**
  <p align="center"><img src="https://i.imgur.com/VQjQPcz.png" height="80%" width="80%" alt="Homelab"/></p>
- Click on `DESKTOP\User` > **Delete** > **Yes** > **OK**
  <p align="center"><img src="https://i.imgur.com/pwUefLd.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/RJ5ICH5.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/2py7ArG.png" height="80%" width="80%" alt="Homelab"/></p>

## Assign a Static IP Address

- Open **Control Panel > Network and Sharing Center > View network status and tasks > Change adapter settings**
  <p align="center"><img src="https://i.imgur.com/ckorJje.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/yOR8dbU.png" height="80%" width="80%" alt="Homelab"/></p>
- Set static IP:  
  - IP: `10.1.10.4`  
  - Subnet: `255.255.255.0`  
  - Gateway: `10.1.10.1`  
  - DNS: `10.1.10.2`
  - Alt DNS: `10.1.10.1`
    <p align="center"><img src="https://i.imgur.com/4umxruM.png" height="80%" width="80%" alt="Homelab"/></p>
- Change **Network Adapter** in VirtualBox to **Host-Only Adapter**
  <p align="center"><img src="https://i.imgur.com/IoalwLP.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/CpcYpqk.png" height="80%" width="80%" alt="Homelab"/></p>
- Test connectivity by pinging `lycatech.com`
  <p align="center"><img src="https://i.imgur.com/DCMMfkR.png" height="80%" width="80%" alt="Homelab"/></p>

## Join Desktop 2 to Domain

- Right-click **This PC** > **Properties > Rename this PC (advanced)**
  <p align="center"><img src="https://i.imgur.com/XfnGjHx.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Change**
  <p align="center"><img src="https://i.imgur.com/Ap1ST4T.png" height="80%" width="80%" alt="Homelab"/></p>
- Enter `lycatech.com` and authenticate with domain admin credentials
  <p align="center"><img src="https://i.imgur.com/gHBto4T.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/JwlS62r.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/47vdl9M.png" height="80%" width="80%" alt="Homelab"/></p>
- Restart your VM
  <p align="center"><img src="https://i.imgur.com/zbZcaGV.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/dvSlDrM.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/6ESb9Bq.png" height="80%" width="80%" alt="Homelab"/></p>
- Verify that the system is in the domain by checking on Server 2016
  <p align="center"><img src="https://i.imgur.com/ksp8aPH.png" height="80%" width="80%" alt="Homelab"/></p>

## Log In as Jason Williams on Desktop2

- On Desktop2, login as user `jwilliams`
  <p align="center"><img src="https://i.imgur.com/dGToUgy.png" height="80%" width="80%" alt="Homelab"/></p>
- Open **Active Directory Users and Computers** on Windows 10 Lab > **HR** > Double-click `Jason Williams` > **Attribute Editor**
  <p align="center"><img src="https://i.imgur.com/Q4vG4HE.png" height="80%" width="80%" alt="Homelab"/></p>
- Confirm last login value has updated
  <p align="center"><img src="https://i.imgur.com/0x3z9ur.png" height="80%" width="80%" alt="Homelab"/></p>
