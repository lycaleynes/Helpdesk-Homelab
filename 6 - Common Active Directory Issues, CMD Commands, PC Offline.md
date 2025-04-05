# Common Active Directory Issues, CMD Commands, PC Offline

## Description

In this lab, we build on previous sessions by exploring common Active Directory (AD) account issues and how to troubleshoot them. You’ll learn how to:

- Unlock user accounts
- Reset and expire passwords
- Enable and disable accounts
- Understand security vs. distribution groups
- Fix trust relationship errors
- Rejoin computers to a domain
- Use helpful CMD commands

## Prerequisites

- Domain controller with Active Directory Users and Computers (ADUC)
- Two Windows 10 machines: Desktop1 (Help Desk) and Desktop2 (User: Jason)
- RSAT tools installed on help desk machine
- User `Jason` already created and joined to domain

## CMD Commands to Know (Run on Jason's Machine)

- Open `cmd`
- Test network connectivity:

```cmd
ping 10.1.10.2
```


## Log In as Patty

- Boot up `Desktop2`
- Log in as `Patty` using password `Welcome1`

---

### Learn the Difference Between Groups

- **Security Group**: Used for permissions like folder access, VPN, Citrix, MFA, etc.
- **Distribution Group**: Used for email distribution (e.g., `it@company.com`)
- Note: Emails from external addresses may need to be explicitly allowed for distribution groups.

---

