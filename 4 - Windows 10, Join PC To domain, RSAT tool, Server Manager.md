# Windows 10, Join PC To domain, RSAT tool, Server Manager

## Description
In this lab, I extended the virtual lab by installing a Windows 10 virtual machine and joining it to the previously created `lycatech.com` domain. This step demonstrates practical skills essential for help desk and desktop support roles, such as domain joining, IP configuration, enabling administrative accounts, and installing Remote Server Administration Tools (RSAT) on Windows 10.

The goal of this lab is to simulate a real-world environment where help desk technicians manage users, troubleshoot domain-related issues, and access Active Directory from client machines without logging directly into the domain controller.

## Lab Environment

- **Platform**: Oracle VirtualBox  
- **Domain Controller**: Windows Server 2016 (`lycatech.com`)  
- **Client Machine**: Windows 10 Pro  
- **Tools & Software**:
  - RSAT Tools (Active Directory, Group Policy, DHCP, DNS)
  - Chrome and TeamViewer (optional utilities)
  - Static IP configuration for isolated lab networking
 
## Download the Windows 10 ISO

- Go to the official [Windows 10 download page](https://www.microsoft.com/en-us/software-download/windows10)
  <p align="center"><img src="https://i.imgur.com/cksICmm.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Download Now**
  <p align="center"><img src="https://i.imgur.com/q0qSELh.png" height="80%" width="80%" alt="Homelab"/></p>
- Run the tool and click **Accept**
  <p align="center"><img src="https://i.imgur.com/qA2Y7Ue.png" height="80%" width="80%" alt="Homelab"/></p>
- Select **Create installation media (ISO)** > **Next**
  <p align="center"><img src="https://i.imgur.com/lNUy6hn.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Next**
  <p align="center"><img src="https://i.imgur.com/tyCpuFp.png" height="80%" width="80%" alt="Homelab"/></p>
- Choose **ISO file** > **Next**
  <p align="center"><img src="https://i.imgur.com/FlVInPV.png" height="80%" width="80%" alt="Homelab"/></p>
- Save the ISO to your chosen folder
  <p align="center"><img src="https://i.imgur.com/MnTvds9.png" height="80%" width="80%" alt="Homelab"/></p>
- Wait for the download to finish
  <p align="center"><img src="https://i.imgur.com/lx8Wvgw.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Finish**
  <p align="center"><img src="https://i.imgur.com/aD3DwI0.png" height="80%" width="80%" alt="Homelab"/></p>

## Create the Windows 10 VM in VirtualBox

- Open VirtualBox and click **New**
- Name it something like `Windows-10-Lab` > Check **Skip Unattended Installation** > **Next**
  <p align="center"><img src="https://i.imgur.com/h9zokEM.png" height="80%" width="80%" alt="Homelab"/></p>
- Assign 4–8 GB of RAM
  <p align="center"><img src="https://i.imgur.com/Zz2aYn3.png" height="80%" width="80%" alt="Homelab"/></p>
- Create a virtual hard disk (50 GB recommended)
  <p align="center"><img src="https://i.imgur.com/eqjU8kF.png" height="80%" width="80%" alt="Homelab"/></p>
- Double check the **Summary** > **Finish**
  <p align="center"><img src="https://i.imgur.com/FmHZT0V.png" height="80%" width="80%" alt="Homelab"/></p>
- Start the VM and boot from the ISO
  <p align="center"><img src="https://i.imgur.com/5CzdoyK.png" height="80%" width="80%" alt="Homelab"/></p>
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

## Configure Static IP Address on Server 2016

- Open **Control Panel > Network and Sharing Center > > View network status and tasks > Change adapter settings**
  <p align="center"><img src="https://i.imgur.com/fXOahcp.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/fUlnnlY.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/uvpJ5j7.png" height="80%" width="80%" alt="Homelab"/></p>
- Select **Internet Protocol Version 4 (TCP/IPv4)** and click **Properties**
  <p align="center"><img src="https://i.imgur.com/sH0dfGU.png" height="80%" width="80%" alt="Homelab"/></p>
- Enter:
  - IP: `10.1.10.2`
  - Subnet mask: `255.255.255.0`
  - Default gateway: `10.1.10.1`
  - Preferred DNS: `10.1.10.2`
  - Alternate DNS: `10.1.10.1`
    <p align="center"><img src="https://i.imgur.com/akCZgAU.png" height="80%" width="80%" alt="Homelab"/></p>
- Click on **Devices** > **Network** > **Network Settings**
  <p align="center"><img src="https://i.imgur.com/ytOccTG.png" height="80%" width="80%" alt="Homelab"/></p>
- Choose **Expert** > Change Attached to: **Host-only Adapter**
  <p align="center"><img src="https://i.imgur.com/BDAvI3K.png" height="80%" width="80%" alt="Homelab"/></p>
- Leave everything as is > Click **OK**
  <p align="center"><img src="https://i.imgur.com/YBYTOgy.png" height="80%" width="80%" alt="Homelab"/></p>

## Setup Windows 10 Lab

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

## Enable Local Administrator Account on Windows 10

- Open **File Explorer** > Right click on **This PC** > **Manage**
  <p align="center"><img src="https://i.imgur.com/SE2WJpO.png" height="80%" width="80%" alt="Homelab"/></p>
- Go to **Local Users and Groups** > **Users**
  <p align="center"><img src="https://i.imgur.com/YtjfVv0.png" height="80%" width="80%" alt="Homelab"/></p>
- Right click on **Administrator** > **Properties**
  <p align="center"><img src="https://i.imgur.com/z88LCRg.png" height="80%" width="80%" alt="Homelab"/></p>
- Uncheck **Account is disabled** > **Apply** > **OK**
  <p align="center"><img src="https://i.imgur.com/ymW6ajd.png" height="80%" width="80%" alt="Homelab"/></p>
- Right click on **Administrator** > **Set Password** > **Proceed**
  <p align="center"><img src="https://i.imgur.com/dECIl5A.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/bWjaJ4w.png" height="80%" width="80%" alt="Homelab"/></p>
- Set a password for your Administrator account > **OK**
  <p align="center"><img src="https://i.imgur.com/vwDo7Jd.png" height="80%" width="80%" alt="Homelab"/></p>
- Sign out from the User account
  <p align="center"><img src="https://i.imgur.com/HZY7Vvv.png" height="80%" width="80%" alt="Homelab"/></p>
- Sign in to your Administrator account
  <p align="center"><img src="https://i.imgur.com/zgAKz6I.png" height="80%" width="80%" alt="Homelab"/></p>
- Delete the User account > **Yes** > **OK**
  <p align="center"><img src="https://i.imgur.com/PPRaFxq.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/0KDnIQo.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/Zc6vvNj.png" height="80%" width="80%" alt="Homelab"/></p>

## Install RSAT Tools on Windows 10

- Search **Add an optional feature** in the search bar
  <p align="center"><img src="https://i.imgur.com/TUk1bVg.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Add a feature**
  <p align="center"><img src="https://i.imgur.com/3CV92lP.png" height="80%" width="80%" alt="Homelab"/></p>
- Search and install:
  - RSAT: Remote Desktop Services Tools
  - RSAT: Server Manager
  - RSAT: DNS Server Tools
  - RSAT: Group Policy Management Tools
  - RSAT: Active Directory Domain Services and LDS
  - RSAT: DHCP Server Tools
  - RSAT: Active Directory Certificate Services Tools
    <p align="center"><img src="https://i.imgur.com/NrYUPQw.png" height="80%" width="80%" alt="Homelab"/></p>
    <p align="center"><img src="https://i.imgur.com/b2f2thW.png" height="80%" width="80%" alt="Homelab"/></p>
- Wait for installation to finish
  <p align="center"><img src="https://i.imgur.com/SlmWwfU.png" height="80%" width="80%" alt="Homelab"/></p>
- Restart the VM
  <p align="center"><img src="https://i.imgur.com/644Ct1h.png" height="80%" width="80%" alt="Homelab"/></p>

## Rename Windows 10 Lab

- Open **File Explorere** > Right click **This PC** > **Properties**
  <p align="center"><img src="https://i.imgur.com/IOYd7KY.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Rename this PC (advanced)**
  <p align="center"><img src="https://i.imgur.com/lXuDULk.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Change**
  <p align="center"><img src="https://i.imgur.com/p8YqZvt.png" height="80%" width="80%" alt="Homelab"/></p>
- Change computer name to `Desktop1` > **OK**
  <p align="center"><img src="https://i.imgur.com/lrCb0Kh.png" height="80%" width="80%" alt="Homelab"/></p>
- Restart the VM
  <p align="center"><img src="https://i.imgur.com/QTmdd1x.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/yBZkpdh.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/yBZkpdh.png" height="80%" width="80%" alt="Homelab"/></p>

## Download Google Chrome and TeamViewer on Windows 10 Lab

- Open **Microsoft Edge**
  <p align="center"><img src="https://i.imgur.com/nmDovlA.png" height="80%" width="80%" alt="Homelab"/></p>
- Go to Chrome's download page and download the browser
  <p align="center"><img src="https://i.imgur.com/P7FNwM9.png" height="80%" width="80%" alt="Homelab"/></p>
- Open the file
  <p align="center"><img src="https://i.imgur.com/vSrwZeX.png" height="80%" width="80%" alt="Homelab"/></p>
- Wait for installation to finish
  <p align="center"><img src="https://i.imgur.com/CcIeec9.png" height="80%" width="80%" alt="Homelab"/></p>
- Open **Google Chrome** > Go to TeamViewer's download page and download the software
  <p align="center"><img src="https://i.imgur.com/Okz3EpR.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/Nxi8PIT.png" height="80%" width="80%" alt="Homelab"/></p>
- Open `TeamViewer_Setup_x64.exe`
  <p align="center"><img src="https://i.imgur.com/2hnzNwK.png" height="80%" width="80%" alt="Homelab"/></p>
- Choose **Default installation** > **Accept - next**
  <p align="center"><img src="https://i.imgur.com/qWad5Gv.png" height="80%" width="80%" alt="Homelab"/></p>
- Accept the EULA and DPA > **Continue**
  <p align="center"><img src="https://i.imgur.com/qXmfZQe.png" height="80%" width="80%" alt="Homelab"/></p>

## Configure Static IP Address on Windows 10

- Open **Control Panel > Network and Sharing Center > Change adapter settings**
- Right-click the network adapter > **Properties**
- Select **Internet Protocol Version 4 (TCP/IPv4)** and click **Properties**
- Enter:
  - IP: `10.1.10.3`
  - Subnet mask: `255.255.255.0`
  - Default gateway: `10.1.10.1`
  - Preferred DNS: `10.1.10.2`
  - Alternate DNS: `10.1.10.1`
    <p align="center"><img src="https://i.imgur.com/qiHESNv.png" height="80%" width="80%" alt="Homelab"/></p>

> 💡 Ensure both the Windows 10 and Server 2016 VMs are set to **Host-Only Adapter** in VirtualBox and are in the same IP range.

## Join the Domain on Windows 10 Lab

- Right-click **This PC** > **Properties > Rename this PC (advanced)**
  <p align="center"><img src="https://i.imgur.com/X0fXOLG.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/HnGREIN.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Change**
  <p align="center"><img src="https://i.imgur.com/2h1mfde.png" height="80%" width="80%" alt="Homelab"/></p>
- Enter `lycatech.com` and authenticate with domain admin credentials
  <p align="center"><img src="https://i.imgur.com/hh0nBUs.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/Uz0eFgx.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/3odNu0M.png" height="80%" width="80%" alt="Homelab"/></p>
- Restart your VM
  <p align="center"><img src="https://i.imgur.com/cETfsJr.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/SUYos3j.png" height="80%" width="80%" alt="Homelab"/></p>
- Verify that the system is in the domain by checking on Server 2016
  <p align="center"><img src="https://i.imgur.com/XCiRVKD.png" height="80%" width="80%" alt="Homelab"/></p>

## Log In with the Domain Help Desk Account

- Go to your Server 2016 > **Active Directory Users and Computers** > **Users** > Right click on **helpdesk** > **Reset Password**
  <p align="center"><img src="https://i.imgur.com/Vc56YSp.png" height="80%" width="80%" alt="Homelab"/></p>
- Reset the password > **OK**
  <p align="center"><img src="https://i.imgur.com/ZZWPbOo.png" height="80%" width="80%" alt="Homelab"/></p>
- At the login screen, click **Other user**
  <p align="center"><img src="https://i.imgur.com/X7eb5er.png" height="80%" width="80%" alt="Homelab"/></p>
- Enter the domain credentials (e.g., `helpdesk`)
  <p align="center"><img src="https://i.imgur.com/BQ0wpdv.png" height="80%" width="80%" alt="Homelab"/></p>

## Verify RSAT Access

- Open Start and search for **Active Directory Users and Computers**
- Confirm you can view your domain and manage users/computers
- Pin it to the taskbar for convenience
  <p align="center"><img src="https://i.imgur.com/bhPUFEV.png" height="80%" width="80%" alt="Homelab"/></p>
