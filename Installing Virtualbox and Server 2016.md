# Installing Virtualbox and Server 2016

## Description

<p>This project walks through the step-by-step setup of a Windows Server 2016 virtual machine. The lab provides exposure to core help desk and IT support concepts, such as system specs assessment, virtualization, ISO image handling, and preparing for Active Directory configuration.</p>

## Lab Environment

- Platform: Oracle VirtualBox (compatible with VMware and other hypervisors)
- Operating System: Windows Server 2016 (ISO from Microsoft Evaluation Center)
- Host Requirements:
  - Minimum 2 GB RAM (recommended 4–8 GB)
  - At least 50 GB available disk space
  - Virtualization enabled in BIOS/UEFI

## Installation Preparation
   - Download and install [VirtualBox](https://www.virtualbox.org/wiki/Downloads) and the Extension Pack.
     <p align="center"><img src="https://i.imgur.com/8yTY2B1.png" height="80%" width="80%" alt="Homelab"/></p>
   - Verify hardware specs via system properties. Go to <b>Settings</b> > <b>System</b> > <b>About</b>.
     <p align="center"><img src="https://imgur.com/dhn0zhn.png" height="80%" width="80%" alt="Homelab"/></p>
   - Enable [virtualization](https://support.microsoft.com/en-us/windows/enable-virtualization-on-windows-c5578302-6e43-4b4b-a449-8ced115f58e1) in BIOS if required.
     <p align="center"><img src="https://i.imgur.com/Wcf1hZ9.png" height="80%" width="80%" alt="Homelab"/></p>

## ISO Acquisition
   - Go to [Microsoft Evaluation Center](https://www.microsoft.com/en-us/evalcenter). Choose whatever version you want. For this lab we will be using Windows Server 2016.
     <p align="center"><img src="https://i.imgur.com/2dpv3ck.png" height="80%" width="80%" alt="Homelab"/></p>
   - Click on [Download the ISO](https://go.microsoft.com/fwlink/p/?linkid=2195684&clcid=0x409&culture=en-us&country=us).
     <p align="center"><img src="https://i.imgur.com/GBcduMM.png" height="80%" width="80%" alt="Homelab"/></p>
   - Register, then download and install. Windows Server 2016 evaluation editions expire in 180 days.
     <p align="center"><img src="https://i.imgur.com/OK4vDcy.png" height="80%" width="80%" alt="Homelab"/></p>
     <p align="center"><img src="https://i.imgur.com/xpMYtk9.png" height="80%" width="80%" alt="Homelab"/></p>

## Installing VirtualBox & Extension Pack
   - Launch the Setup Wizard. You’ll see a welcome screen for the Oracle VirtualBox 7.1.6 Setup Wizard → Click Next.
     <p align="center"><img src="https://i.imgur.com/VdvC0rk.png" height="80%" width="80%" alt="Homelab"/></p>
   - Accept the License Agreement. Read through the license terms → Select "I accept the terms in the License Agreement" → Click Next.
     <p align="center"><img src="https://i.imgur.com/9AGJyKU.png" height="80%" width="80%" alt="Homelab"/></p>
   - Choose Installation Components. Select which VirtualBox features to install. You can also change the installation location → Click Next.
     <p align="center"><img src="https://i.imgur.com/WOvcDSw.png" height="80%" width="80%" alt="Homelab"/></p>
   - Network Interfaces Warning. You’re notified that the networking feature will reset your network temporarily → Click Yes to proceed.
     <p align="center"><img src="https://i.imgur.com/psnICMV.png" height="80%" width="80%" alt="Homelab"/></p>
   - Python Bindings Warning. If Python Core/win32api dependencies are missing, you’ll be prompted → Click Yes to continue (or install those dependencies later if needed).
     <p align="center"><img src="https://i.imgur.com/s1LY1a5.png" height="80%" width="80%" alt="Homelab"/></p>
   - Select Additional Tasks. Choose setup options → Click Next.
     <p align="center"><img src="https://i.imgur.com/QzONKuc.png" height="80%" width="80%" alt="Homelab"/></p>
   - Ready to Install. Setup confirms that it’s ready to begin installing VirtualBox with your selected options → Click Install.
     <p align="center"><img src="https://i.imgur.com/hzG3KtM.png" height="80%" width="80%" alt="Homelab"/></p>
   - Installation Progress. VirtualBox will install and show progress (e.g., writing registry values) → Wait until the installation completes.
     <p align="center"><img src="https://i.imgur.com/l6czBh3.png" height="80%" width="80%" alt="Homelab"/></p>
   - Install the Extension Pack. A prompt appears asking to install the Oracle VirtualBox Extension Pack, which adds advanced features → Click Install to continue.
     <p align="center"><img src="https://i.imgur.com/whq3u1U.png" height="80%" width="80%" alt="Homelab"/></p>
   - Accept the License Agreement for Extension Pack. The license agreement for the extension pack is shown → Scroll through the text to review the terms → Click I Agree to proceed with installation.
     <p align="center"><img src="https://i.imgur.com/ADqXQbG.png" height="80%" width="80%" alt="Homelab"/></p>

## Virtual Machine Setup
   - Name and Operating System. Define the virtual machine’s basic settings:
     - Name: Enter a name for the VM (e.g., ``Server-2016-Lab``).
     - Folder: Choose where the VM files will be stored.
     - ISO Image: Select the Windows Server 2016 ISO file you've downloaded earlier.
     - VirtualBox will auto-detect the OS edition and version.
     - Don't forget to check ``Skip Unattended Install`` → Click Next.
     <p align="center"><img src="https://i.imgur.com/XgAlHWi.png" height="80%" width="80%" alt="Homelab"/></p>
   - Configure Hardware Settings. Adjust the virtual hardware allocation:
     - Base Memory: Set RAM (e.g., 8192 MB)
     - Processors: Select number of CPU cores (e.g., 1 CPU) → Optional: Enable EFI if required by the OS → Click Next
     <p align="center"><img src="https://i.imgur.com/Jp6O3pN.png" height="80%" width="80%" alt="Homelab"/></p>
   - Virtual Hard Disk. Create or attach a virtual hard disk:
     - Create a Virtual Hard Disk Now is selected
     - Disk Size: Adjust as needed (e.g., 50.00 GB) → Click Next
     <p align="center"><img src="https://i.imgur.com/Mr3gkL6.png" height="80%" width="80%" alt="Homelab"/></p>

## Windows Server Installation:
   - Choose Language and Input Settings → Click Next
     <p align="center"><img src="https://i.imgur.com/YPTRkyN.png" height="80%" width="80%" alt="Homelab"/></p>
   - Click Install now to begin the setup process.
     <p align="center"><img src="https://i.imgur.com/Ma8ecEL.png" height="80%" width="80%" alt="Homelab"/></p>
   - Choose an operating system version → Recommended: Windows Server 2016 Standard Evaluation (Desktop Experience) for a GUI → Click Next
     <p align="center"><img src="https://i.imgur.com/4JIbx5q.png" height="80%" width="80%" alt="Homelab"/></p>
   - Check the box for I accept the license terms → Click Next
     <p align="center"><img src="https://i.imgur.com/e90X7pq.png" height="80%" width="80%" alt="Homelab"/></p>
   - Select Custom: Install Windows only (advanced) to perform a clean install.
     <p align="center"><img src="https://i.imgur.com/dUgxJMQ.png" height="80%" width="80%" alt="Homelab"/></p>
   - Choose the virtual hard disk (e.g., 50.0 GB unallocated space) → Click Next
     <p align="center"><img src="https://i.imgur.com/fagMXuZ.png" height="80%" width="80%" alt="Homelab"/></p>
   - The installer copies files and prepares Windows. This may take several minutes.
     <p align="center"><img src="https://i.imgur.com/QsdLlzR.png" height="80%" width="80%" alt="Homelab"/></p>
   - Once setup finishes, you’ll be asked to configure a password for the built-in Administrator account → Enter and confirm the password → Click Finish
     <p align="center"><img src="https://i.imgur.com/Y9cyiI1.png" height="80%" width="80%" alt="Homelab"/></p>
   - You’ll reach the login screen → Use the VirtualBox menu: Input > Keyboard > Insert Ctrl+Alt+Del → Log in with the Administrator account
     <p align="center"><img src="https://i.imgur.com/egR9OuE.png" height="80%" width="80%" alt="Homelab"/></p>
   - After logging in, Server Manager launches automatically, allowing you to configure roles, features, and system settings.
     <p align="center"><img src="https://i.imgur.com/uD5jh0v.png" height="80%" width="80%" alt="Homelab"/></p>
