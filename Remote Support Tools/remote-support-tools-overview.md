# 🛠️ Remote Support Tools Overview

[ Back to Overview] → [README.md](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/README.md)

---

## 📋 Summary

IT support technicians often need to investigate a computer without walking to it. This section covers four ways to reach and examine remote Windows computers in the `seemaenterprise.co.in` lab on Azure: Remote Desktop, Remote Computer Management, Remote Event Viewer and UNC path access.

---

## 💡 What Are Remote Support Tools?

Remote support tools let a technician reach another computer over the network. Some give full control of the desktop, and others give only an administrative console or file access. Choosing the lightest tool that solves the problem is faster and less disruptive for the user.

| Setting | Value |
|---------|-------|
| **Platform** | Microsoft Azure |
| **Admin machine** | Windows 11 client VM |
| **Target machines** | Windows 11 client VM and `server2021` (Windows Server, Domain Controller and file server) |
| **Domain** | `seemaenterprise.co.in` |
| **Test user** | `Sam` |

---

## 🗂️ Tools in This Section

| Tool | What it does | How to open | Port | Lab file |
|------|--------------|-------------|------|----------|
| **Remote Desktop (RDP)** | Shows and controls the remote desktop | `mstsc` | TCP 3389 | [Remote Desktop Protocol](./remote-desktop-rdp.md) |
| **Remote Computer Management** | Manages services, shares and disks without a desktop session | `compmgmt.msc` → Connect to another computer | RPC and SMB (TCP 445) | [Remote Computer Management](./remote-computer-management.md) |
| **Remote Event Viewer** | Reads the event logs of the remote computer | `eventvwr.msc` → Connect to another computer | RPC | [Remote Event Viewer](./remote-event-viewer.md) |
| **UNC Path Access** | Opens a shared folder over the network | Run → `\\server2021\Companyshare` | TCP 445 (SMB) | [UNC Path Access](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Remote%20Support%20Tools/unc-path-access.md) |

> **Note:** Computer Management and Event Viewer are administrative consoles, not remote-control applications. They let you investigate a computer without taking over its desktop.

---

## 🎯 Choosing the Right Tool

| Need | Use |
|------|-----|
| See what the user sees, or work on the desktop | Remote Desktop |
| Check or restart a service, check shares or disks | Remote Computer Management |
| Find out why a computer crashed, restarted or failed a sign-in | Remote Event Viewer |
| Check that a shared folder is reachable and the permissions work | UNC Path Access |





---

## 💡 Next Step

→ [Event Viewer – Windows Server Troubleshooting Projects](https://github.com/seemasm20-source/Windows-Server-Azure-AD/tree/main/Event%20Viewer)
