# Using Ticketing Systems and Remote Support Tools

## Overview

This lab introduces ticketing systems and remote support tools in IT environments. You'll learn the purpose and flow of help desk tickets, how to document issues and resolutions, and how to perform remote desktop support using Spiceworks and Zoho Assist.

## Objectives

- Understand the role of ticketing systems in IT support
- Create, assign, and close tickets using Spiceworks Help Desk
- Practice documentation and escalation procedures
- Use Zoho Assist for remote support sessions

## Ticketing System: Spiceworks Help Desk

### Why Ticketing Systems Are Used

- Track and manage IT issues efficiently
- Assign work to the appropriate team or technician
- Document problem resolution for future reference
- Ensure accountability and timely responses

### Spiceworks Setup

- Go to [spiceworks.com](https://www.spiceworks.com)
  <p align="center"><img src="https://i.imgur.com/8LG4eok.png" height="80%" width="80%" alt="Homelab"/></p>
- Create a free account
  <p align="center"><img src="https://i.imgur.com/sAim8Ol.png" height="80%" width="80%" alt="Homelab"/></p>
  <p align="center"><img src="https://i.imgur.com/7H1zG29.png" height="80%" width="80%" alt="Homelab"/></p>
- Launch **Cloud Help Desk**
  <p align="center"><img src="https://i.imgur.com/4UUNq3Z.png" height="80%" width="80%" alt="Homelab"/></p>
- Set up your organization’s Help Desk portal
  <p align="center"><img src="https://i.imgur.com/dK6DMgD.png" height="80%" width="80%" alt="Homelab"/></p>

### Creating and Managing Tickets

- Click **Create a Ticket**
- Fill in details:
   - Issue summary
   - Description
   - User and device involved
   - Priority level
- Assign to a team member (or yourself)
- Save and track progress
- Upon resolution, **close the ticket** with brief notes explaining the fix

### Notes on Ticket Handling

- Understand your team’s **policies and procedures**
- Escalate appropriately (e.g., network issue → Network Admin)
- Always leave **concise documentation** when closing a ticket

## Remote Support with Zoho Assist

### Why Remote Sessions Matter

- Enable quick troubleshooting for remote users
- Save time vs. walking users through issues manually
- Useful for installing software, configuring settings, or gathering logs

### Setting Up a Zoho Assist Session

- Go to [join.zoho.com](https://join.zoho.com)
  <p align="center"><img src="https://i.imgur.com/gCELwaR.png" height="80%" width="80%" alt="Homelab"/></p>
- Generate a **session ID** in Zoho Assist
  <p align="center"><img src="https://i.imgur.com/vK2C0d3.png" height="80%" width="80%" alt="Homelab"/></p>
- On the user’s PC (e.g., Desktop2/Jason):
   - Launch browser, enter session ID
   - Download and run the Zoho Assist client
     <p align="center"><img src="https://i.imgur.com/sSkzFk3.png" height="80%" width="80%" alt="Homelab"/></p>
     <p align="center"><img src="https://i.imgur.com/6JbzUgT.png" height="80%" width="80%" alt="Homelab"/></p>
     <p align="center"><img src="https://i.imgur.com/bJ7aZW4.png" height="80%" width="80%" alt="Homelab"/></p>
     <p align="center"><img src="https://i.imgur.com/0suiWbT.png" height="80%" width="80%" alt="Homelab"/></p>
- You gain remote access to the user’s session
  <p align="center"><img src="https://i.imgur.com/hHphC3R.png" height="80%" width="80%" alt="Homelab"/></p>
- Perform tasks like:
   - Open CMD or Control Panel
   - Transfer files (e.g., VPN clients)
   - Use chat to communicate
   - Elevate to admin rights for deeper access (if needed)
  
### Example Use Case

- User cannot open Zoom due to a missing file
- Help desk launches remote session
- Transfers installer file via Zoho
- Installs the app and confirms resolution
- Documents fix in the related Spiceworks ticket
