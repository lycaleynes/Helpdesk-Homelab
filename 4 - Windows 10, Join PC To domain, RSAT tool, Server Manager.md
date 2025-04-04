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
- Click **Download Tool Now**
- Run the tool and select **Create installation media (ISO)**
- Save the ISO to your desktop or downloads folder

## Create the Windows 10 VM in VirtualBox

- Open VirtualBox and click **New**
- Name it something like `Windows 10 Client`
- Assign 4–8 GB of RAM
- Create a virtual hard disk (50 GB recommended)
- Start the VM and boot from the ISO
- Install **Windows 10 Pro** (not Home)
- Create a local account with a password like `Welcome1`

## Configure Static IP Address on Windows 10

- Open **Control Panel > Network and Sharing Center > Change adapter settings**
- Right-click the network adapter > **Properties**
- Select **Internet Protocol Version 4 (TCP/IPv4)** and click **Properties**
- Enter:
  - IP: `10.1.10.3`
  - Subnet mask: `255.255.255.0`
  - Default gateway: `10.1.10.1`
  - Preferred DNS: `10.1.10.2`

> 💡 Ensure both the Windows 10 and Server 2016 VMs are set to **Host-Only Adapter** in VirtualBox and are in the same IP range.

## Enable Local Administrator Account (Optional)

- Open **Computer Management > Local Users and Groups > Users**
- Right-click the `Administrator` account > **Properties**
- Uncheck **Account is disabled**
- Set a password and log in using this account

## Install RSAT Tools on Windows 10

- Open **Settings > Apps > Optional Features**
- Click **Add a feature**
- Search and install:
  - RSAT: Active Directory Domain Services and LDS
  - RSAT: DHCP Server Tools
  - RSAT: DNS Server Tools
  - RSAT: Group Policy Management Tools
  - RSAT: Server Manager
- Restart the VM

## Rename the Computer and Join the Domain

- Right-click **This PC** > **Properties > Rename this PC**
- Rename it to `DESKTOP1` and restart
- Go back to the same menu and click **Join a domain**
- Enter `kevtech.com` and authenticate with domain admin credentials
- Restart once again

## Log In with the Domain Help Desk Account

- At the login screen, click **Other user**
- Enter the domain credentials (e.g., `helpdesk`)
- Verify that it shows `Sign in to: kevtech.com`

## Verify RSAT Access

- Open Start and search for **Active Directory Users and Computers**
- Confirm you can view your domain and manage users/computers
- Pin it to the taskbar for convenience
