# Windows 10 Remote, Remote Registry, Remote Desktop, C$

## Overview

In this lab, we expand our IT support capabilities by exploring multiple methods for remotely accessing a user machine. We use the existing environment from Lab 7 with the user account `Jason` on `Desktop2` and `HelpDesk` on `Desktop1`. The goal is to practice safe and effective remote support operations in a Windows domain environment.

---

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
- Under **Remote Desktop**, select **Allow remote connections to this computer**
- Add `HelpDesk` user under **Select Users** > **Add** > enter `HelpDesk`
- Apply changes and click OK

---

## Remote Desktop to Desktop2 as HelpDesk

- On `Desktop1`, open **Remote Desktop Connection**
- Connect to: `Desktop2`
- Authenticate as `HelpDesk`
- Observe the ability to browse `Jason`'s user folders: Desktop, Downloads, AppData

### Why this is Useful:
- Allows troubleshooting without needing user to be present
- You can delete or move corrupted files in their profile
- You can review configuration files like Outlook or Skype in AppData

---

## File Transfer via C$ Administrative Share

- On `Desktop1`, open File Explorer > type `\\Desktop2\C$`
- Navigate to: `Users\jwilliams\Desktop`
- Drag-and-drop files to and from this location

### Notes:
- Requires proper credentials and Remote Admin rights
- Useful for repairing broken desktop shortcuts, corrupt files, etc.

---

## Identify User Mapped Drives (Two Methods)

### Method 1: CMD (Net Use)

- On `Jason`’s machine, open **CMD**
- Run: `net use`
- Displays mapped drives like `Z:` (HR share) and `P:` (Personal drive)

### Method 2: Remote Registry (From HelpDesk)

- Open **regedit** as `HelpDesk`
- File > Connect Network Registry > `Desktop2`
- Navigate to:
  - `HKEY_USERS`
  - Find SID for Jason
  - Go to `Network` key to view drive letters and mapped shares

---

## Enable Remote Registry Service (if needed)

- On `Desktop2`, open **Services** > locate **Remote Registry**
- Right-click > **Properties** > set to **Automatic**, click **Start**

---

## Use Windows Remote Assistance (GUI Tool)

### On User Machine (Jason):
- Open Start > **Windows Remote Assistance**
- Select: **Invite someone you trust to help**
- Save invitation file to Desktop
- Communicate security code to HelpDesk

### On HelpDesk Machine:
- Open Remote Assistance > **Help someone who invited you**
- Open saved invitation file
- Enter provided security code
- Request control > Wait for user to approve

### Use Cases:
- View live desktop activity
- Send text chat messages
- Request full control for troubleshooting

---

## Recap

- Enabled and tested Remote Desktop login with `HelpDesk`
- Navigated and edited files in Jason’s profile
- Used `net use`, regedit, and C$ shares for troubleshooting
- Practiced secure, GUI-based remote assistance

---

## What’s Next

- Build user restrictions and access policies via Group Policy
- Practice scripting remote actions (PowerShell)
- Explore advanced endpoint management tools

---

**Tip:** Add this to your resume under "Skills":

> Supported end users via Remote Desktop and Windows Remote Assistance; performed remote file recovery, registry diagnostics, and mapped drive troubleshooting.

---

Stay tuned for Lab 9, where we apply Group Policy to control desktop environments and enforce security standards.

