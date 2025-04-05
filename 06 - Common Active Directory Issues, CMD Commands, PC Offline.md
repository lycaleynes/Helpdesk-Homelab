# Common Active Directory Issues, CMD Commands, PC Offline

## Description

In this lab, we build on previous sessions by exploring common Active Directory (AD) account issues and how to troubleshoot them. You’ll learn how to:

- Unlock user accounts
- Reset and expire passwords
- Enable and disable accounts
- Rejoin computers to a domain
- Use helpful CMD commands

## Prerequisites

- Domain controller with Active Directory Users and Computers (ADUC)
- Two Windows 10 machines: Desktop1 (Help Desk) and Desktop2 (User: Jason)
- RSAT tools installed on help desk machine
- User `Jason` already created and joined to domain

## CMD Commands to Know (Run on Jason's Machine)

- Open `cmd`

```cmd
ping 10.1.10.2
```
Sends ICMP echo requests to the IP address `10.1.10.2` to test network connectivity.
<p align="center"><img src="https://i.imgur.com/NpN4tND.png" height="80%" width="80%" alt="Homelab"/></p>

```cmd
ping 10.1.10.2 -t
```
Continuously sends ICMP echo requests to `10.1.10.2` until you manually stop it (with Ctrl + C).
<p align="center"><img src="https://i.imgur.com/ZAKGgvI.png" height="80%" width="80%" alt="Homelab"/></p>

```cmd
ipconfig
```
Displays IP configuration details for all network adapters on the system.
<p align="center"><img src="https://i.imgur.com/TCGa2qC.png" height="80%" width="80%" alt="Homelab"/></p>

- Run `cmd` as administrator
  <p align="center"><img src="https://i.imgur.com/DjGNfTI.png" height="80%" width="80%" alt="Homelab"/></p>

```cmd
gpresult /r >c:\results.txt
```
Generates a summary of Group Policy settings applied to the user and computer, then saves the output to a file called `results.txt` in the `C:\` drive.
<p align="center"><img src="https://i.imgur.com/I54XyeF.png" height="80%" width="80%" alt="Homelab"/></p>

- Open **File Explorer** > **Local Disk (C:)** > Open `results`
  <p align="center"><img src="https://i.imgur.com/1ppPkxQ.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/u1YvJVJ.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/vLqkAdm.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/MGsYGRA.png" height="80%" width="80%" alt="Homelab"/></p>

```cmd
gpupdate /help
```
Displays help information for the `gpupdate` command, including available options and how to use them.
<p align="center"><img src="https://i.imgur.com/Gkz7iht.png" height="80%" width="80%" alt="Homelab"/></p>

```cmd
gpresult /?
```
Displays help and usage information for the `gpresult` command, listing all available switches and syntax.
<p align="center"><img src="https://i.imgur.com/kWdjkJr.png" height="80%" width="80%" alt="Homelab"/></p>

```cmd
gpresult /r
```
Displays a summary of Group Policy settings applied to the current user and computer.
<p align="center"><img src="https://i.imgur.com/8Os9Ehz.png" height="80%" width="80%" alt="Homelab"/></p>

```cmd
gpresult /h gpreport.html
```
Generates a Group Policy report in HTML format and saves it as `gpreport.html`.
<p align="center"><img src="https://i.imgur.com/yBjDL8S.png" height="80%" width="80%" alt="Homelab"/></p>

## Unlock User Accounts

<p align="center"><img src="https://i.imgur.com/7i8ct8L.png" height="80%" width="80%" alt="Homelab"/></p>

- Go to **Active Directory Users and Computers** on Server 2016 > **HR**
  <p align="center"><img src="https://i.imgur.com/XqV2X7F.png" height="80%" width="80%" alt="Homelab"/></p>
- Double-click **Jason Williams**
  <p align="center"><img src="https://i.imgur.com/zNdl22t.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Account**
  <p align="center"><img src="https://i.imgur.com/RwKNfbD.png" height="80%" width="80%" alt="Homelab"/></p>
- Check **Unlock account** > **OK**
  <p align="center"><img src="https://i.imgur.com/dg1Dd2P.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/gr1Z587.png" height="80%" width="80%" alt="Homelab"/></p>
- Log back in to Jason Williams' account
  <p align="center"><img src="https://i.imgur.com/0Mcrzcl.png" height="80%" width="80%" alt="Homelab"/></p>

## Enable and Disable Accounts

- Go to **Active Directory Users and Computers** on Server 2016 > **HR** > Right-click **Jason Williams** > **Disable Account**
  <p align="center"><img src="https://i.imgur.com/zdBusdA.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/mAjdde9.png" height="80%" width="80%" alt="Homelab"/></p>
- Right-click domain root > **Find**
  <p align="center"><img src="https://i.imgur.com/X3AaeYp.png" height="80%" width="80%" alt="Homelab"/></p>
- Type `jason` > **Find Now**
  <p align="center"><img src="https://i.imgur.com/wx4F8DY.png" height="80%" width="80%" alt="Homelab"/></p>
- Right-click on `Jason Williams` > **Enable Account**
  <p align="center"><img src="https://i.imgur.com/DSXWAgg.png" height="80%" width="80%" alt="Homelab"/></p>
- Log back in to Jason Williams' account
  <p align="center"><img src="https://i.imgur.com/0Mcrzcl.png" height="80%" width="80%" alt="Homelab"/></p>

## Resetting Passwords

- Right-click domain root > **Find**
  <p align="center"><img src="https://i.imgur.com/X3AaeYp.png" height="80%" width="80%" alt="Homelab"/></p>
- Type `jason` > **Find Now**
  <p align="center"><img src="https://i.imgur.com/wx4F8DY.png" height="80%" width="80%" alt="Homelab"/></p>
- Right-click on `Jason Williams` > **Reset Password**
  <p align="center"><img src="https://i.imgur.com/g6BzIAH.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/ayhs3Pt.png" height="80%" width="80%" alt="Homelab"/></p>
- Log back in to Jason Williams' account
  <p align="center"><img src="https://i.imgur.com/0Mcrzcl.png" height="80%" width="80%" alt="Homelab"/></p>

## Expired Accounts

- Right-click domain root > **Find**
  <p align="center"><img src="https://i.imgur.com/X3AaeYp.png" height="80%" width="80%" alt="Homelab"/></p>
- Type `jason` > **Find Now**
  <p align="center"><img src="https://i.imgur.com/wx4F8DY.png" height="80%" width="80%" alt="Homelab"/></p>
- Double-click `Jason Williams` > **Account** > Under **Account expires**, click **End of:** and set date to `Friday, December 15, 2000`
  <p align="center"><img src="https://i.imgur.com/B1y0qhN.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/sdh2gAM.png" height="80%" width="80%" alt="Homelab"/></p>
- Go back to `Jason Williams` > **Account** > Under **Account expires**, click **Never**
  <p align="center"><img src="https://i.imgur.com/QmK9LQC.png" height="80%" width="80%" alt="Homelab"/></p>
- Log back in to Jason Williams' account
  <p align="center"><img src="https://i.imgur.com/0Mcrzcl.png" height="80%" width="80%" alt="Homelab"/></p>

## Disabled Computer

- Go back to Server 2016 > **Computers** > Right click **DESKTOP2** > **Disable Account**
  <p align="center"><img src="https://i.imgur.com/CrR47ER.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/6Y76SDJ.png" height="80%" width="80%" alt="Homelab"/></p>
- Go back to Server 2016 > **Computers** > Right click **DESKTOP2** > **Enable Account**
  <p align="center"><img src="https://i.imgur.com/R3l2d3f.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/dMyayy3.png" height="80%" width="80%" alt="Homelab"/></p>
- Log back in to Jason Williams' account
  <p align="center"><img src="https://i.imgur.com/eI7ef5A.png" height="80%" width="80%" alt="Homelab"/></p>

## Rejoining Deleted Computer to Domain

- Go back to Server 2016 > **Computers** > Right click **DESKTOP2** > **Delete**
  <p align="center"><img src="https://i.imgur.com/avmzway.png" height="80%" width="80%" alt="Homelab"/></p>
- Make a New User called `Test`
  <p align="center"><img src="https://i.imgur.com/yPCWdS6.png" height="80%" width="80%" alt="Homelab"/></p>
- Use `Test` to log in to Desktop 2. It should show the following:
  <p align="center"><img src="https://i.imgur.com/gUZemnk.png" height="80%" width="80%" alt="Homelab"/></p>
- Login using `.\administrator`
  <p align="center"><img src="https://i.imgur.com/U1zNXga.png" height="80%" width="80%" alt="Homelab"/></p>
- Go to **File Explorer** > Right-click **This PC** > **Properties**
  <p align="center"><img src="https://i.imgur.com/sKdrFUl.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Rename this PC (advanced)**
  <p align="center"><img src="https://i.imgur.com/2dhrwFt.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Change**
  <p align="center"><img src="https://i.imgur.com/cJW1M6I.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **Workgroup** > Type `WORKGROUP`
  <p align="center"><img src="https://i.imgur.com/DF7Rnxy.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **OK**
  <p align="center"><img src="https://i.imgur.com/BOBZ7xV.png" height="80%" width="80%" alt="Homelab"/></p>
- Use `helpdesk` credentials > **OK**
  <p align="center"><img src="https://i.imgur.com/YOBhVpm.png" height="80%" width="80%" alt="Homelab"/></p>
- Click **OK**
  <p align="center"><img src="https://i.imgur.com/S2WzjdO.png" height="80%" width="80%" alt="Homelab"/></p>
- Restart the VM
  <p align="center"><img src="https://i.imgur.com/UlthVBI.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/bqzeOBH.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/eGa8SOT.png" height="80%" width="80%" alt="Homelab"/></p>
- Go back and revert back the domain
  <p align="center"><img src="https://i.imgur.com/1d85IXS.png" height="80%" width="80%" alt="Homelab"/></p>
- Restart the VM
  <p align="center"><img src="https://i.imgur.com/d19JOY3.png" height="80%" width="80%" alt="Homelab"/></p>
- Go to Server 2016 > Right-click > Refresh
  <p align="center"><img src="https://i.imgur.com/9UZrANm.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/Boq8Vui.png" height="80%" width="80%" alt="Homelab"/></p>
