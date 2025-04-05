# Windows 10 Remote, Remote Registry, Remote Desktop, C$

## Overview

In this lab, we expand our IT support capabilities by exploring multiple methods for remotely accessing a user machine. We use the existing environment from Lab 7 with the user account `Jason` on `Desktop2` and `Administrator` on `Server 2016`. The goal is to practice safe and effective remote support operations in a Windows domain environment.

## Objectives

- Enable Remote Desktop on client computers
- Use RDP (Remote Desktop Protocol) to log in as a support user
- Transfer files between user profiles
- Remotely view mapped drives via Registry Editor
- Use C$ administrative share for file access
- Practice Windows Remote Assistance

## Enable Remote Desktop on Desktop2 (Jason’s Machine)

- Log in to `Desktop2` as `Jason`
- Right-click **This PC** > **Properties** > **Remote settings**
    <p align="center"><img src="https://i.imgur.com/irBPcvN.png" height="80%" width="80%" alt="Homelab"/></p>
- Scroll down > Click **Advanced system settings**
  <p align="center"><img src="https://i.imgur.com/vuKqizZ.png" height="80%" width="80%" alt="Homelab"/></p>
- Log in with an admin account
  <p align="center"><img src="https://i.imgur.com/UNzIOE6.png" height="80%" width="80%" alt="Homelab"/></p>
- Under **Remote Desktop**, select **Allow remote connections to this computer** > **Apply** > **OK**
  <p align="center"><img src="https://i.imgur.com/eYwrse2.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/97cd4RP.png" height="80%" width="80%" alt="Homelab"/></p>

## Remote Desktop to Desktop2 as HelpDesk

- On `Server 2016`, open **Remote Desktop Connection**
  <p align="center"><img src="https://i.imgur.com/tkxMEMB.png" height="80%" width="80%" alt="Homelab"/></p>
- Connect to: `Desktop2`
  <p align="center"><img src="https://i.imgur.com/UWJBSh8.png" height="80%" width="80%" alt="Homelab"/></p>
- Authenticate as `Administrator`
  <p align="center"><img src="https://i.imgur.com/L4npdLg.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Yes**
  <p align="center"><img src="https://i.imgur.com/3n1Ockc.png" height="80%" width="80%" alt="Homelab"/></p>
- On `Desktop2`, click **OK**
  <p align="center"><img src="https://i.imgur.com/MvdKIsG.png" height="80%" width="80%" alt="Homelab"/></p>
- Observe the ability to browse `Jason`'s user folders: Desktop, Downloads, AppData
  <p align="center"><img src="https://i.imgur.com/Vmz5Bbv.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/O8jDT6O.png" height="80%" width="80%" alt="Homelab"/></p>
- Disconnect from the remote session
  <p align="center"><img src="https://i.imgur.com/H3jIAbj.png" height="80%" width="80%" alt="Homelab"/></p>

### Why this is Useful:
- Allows troubleshooting without needing user to be present
- You can delete or move corrupted files in their profile
- You can review configuration files like Outlook or Skype in AppData

## Identify User Mapped Drives (Two Methods)

### Method 1: CMD (Net Use)

- On `Jason`’s machine, open **CMD**
- Run: `net use`
- Displays mapped drives like `Z:` (HR share) and `P:` (Personal drive)
  <p align="center"><img src="https://i.imgur.com/wGQ4KN7.png" height="80%" width="80%" alt="Homelab"/></p>

### Method 2: Remote Registry (From HelpDesk)

- Open **regedit** as `HelpDesk`
  <p align="center"><img src="https://i.imgur.com/cIMKwb7.png" height="80%" width="80%" alt="Homelab"/></p>
- File > Connect Network Registry > `Desktop2`
  <p align="center"><img src="https://i.imgur.com/LZ4fIfq.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/eMO0igQ.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/zLVyyh5.png" height="80%" width="80%" alt="Homelab"/></p>
- On `Desktop2`, open **Services** > locate **Remote Registry**
- Right-click > **Properties** > set to **Automatic** > **Apply**
  <p align="center"><img src="https://i.imgur.com/F8wqygX.png" height="80%" width="80%" alt="Homelab"/></p>
- Try connecting to `Desktop2` again
- Navigate to:
  - `HKEY_USERS`
  - Find SID for Jason
  - Go to `Network` key to view drive letters and mapped shares
    <p align="center"><img src="https://i.imgur.com/bSATskX.png" height="80%" width="80%" alt="Homelab"/></p>

## File Transfer via C$ Administrative Share

- On `Desktop1`, open File Explorer > type `\\Desktop2\C$`
  <p align="center"><img src="https://i.imgur.com/0HxzFPw.png" height="80%" width="80%" alt="Homelab"/></p>
- Navigate to: `Users\jwilliams\Desktop`
  <p align="center"><img src="https://i.imgur.com/IhVCKeF.png" height="80%" width="80%" alt="Homelab"/></p>
- Drag-and-drop files to and from this location

### Notes:
- Requires proper credentials and Remote Admin rights
- Useful for repairing broken desktop shortcuts, corrupt files, etc.

## Use Windows Remote Assistance (GUI Tool)

- On `Desktop1`, open **Control Panel** > **System and Security**
  <p align="center"><img src="https://i.imgur.com/IhVCKeF.png" height="80%" width="80%" alt="Homelab"/></p>
- Under **System**, click **Launch remote assistance**
  <p align="center"><img src="https://i.imgur.com/nIr4C7m.png" height="80%" width="80%" alt="Homelab"/></p>
- Choose **Help someone who has invited you**
  <p align="center"><img src="https://i.imgur.com/gwjM7El.png" height="80%" width="80%" alt="Homelab"/></p>
- On `Desktop2`, Launch remote assistance > **Invite someone you trust to help you**
  <p align="center"><img src="https://i.imgur.com/G6YGnv6.png" height="80%" width="80%" alt="Homelab"/></p>
- Choose **Save this invitation as a file**
  <p align="center"><img src="https://i.imgur.com/KMwpUyu.png" height="80%" width="80%" alt="Homelab"/></p>
- Save on your **Desktop**
  <p align="center"><img src="https://i.imgur.com/E80dbrK.png" height="80%" 
- Go back to `Desktop1` > Choose **Use an invitation file**
  <p align="center"><img src="https://i.imgur.com/C9zOZ8D.png" height="80%" width="80%" alt="Homelab"/></p>
- Navigate to `\\Desktop2\C$`
  <p align="center"><img src="https://i.imgur.com/yko9zGM.png" height="80%" width="80%" alt="Homelab"/></p>
- Click the invitation
  <p align="center"><img src="https://i.imgur.com/cavrrMu.png" height="80%" width="80%" alt="Homelab"/></p>
- Enter the password shown on `Desktop2`
  <p align="center"><img src="https://i.imgur.com/Zsu9a3L.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/i9xtQLJ.png" height="80%" width="80%" alt="Homelab"/></p>
- On `Desktop2`, click **Yes**
  <p align="center"><img src="https://i.imgur.com/5zgmlz9.png" height="80%" width="80%" alt="Homelab"/></p>
- Now you can see `Desktop2`'s screen
  <p align="center"><img src="https://i.imgur.com/AGeKaMc.png" height="80%" width="80%" alt="Homelab"/></p>
- Send text chat messages
  <p align="center"><img src="https://i.imgur.com/cDuracJ.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/Mk3qdzi.png" height="80%" width="80%" alt="Homelab"/></p>
- Request control from `Desktop1` > Click **Yes** on `Desktop2`
   <p align="center"><img src="https://i.imgur.com/96ELSyT.png" height="80%" width="80%" alt="Homelab"/></p>
   
### Use Cases:
- View live desktop activity
- Send text chat messages
- Request full control for troubleshooting
