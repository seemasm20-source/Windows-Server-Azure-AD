# 🖥️ Server Manager Overview

[ Back to Overview] → [README.md](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/README.md)

---

## 📋 Summary

After connecting to the Windows Server VM with Remote Desktop, **Server Manager** is the main console for managing the server. It is used to check server status, add roles and features, and open administration tools. In this lab it is used to install Active Directory Domain Services and promote the server to a Domain Controller.

---

## 💡 What is Server Manager?

Server Manager is a built-in Windows Server tool for managing local and remote servers from one place. It opens automatically when an administrator signs in.

| Area | Purpose |
|------|---------|
| **Dashboard** | Overview of the server, its roles and its status |
| **Local Server** | Computer name, IP address, Windows Update, firewall, Remote Desktop and time zone settings |
| **All Servers** | Servers that this console manages |
| **File and Storage Services** | Disks, volumes and shared folders |
| **Manage menu** | Add roles and features, add servers, create server groups |
| **Tools menu** | Shortcuts to administration tools, such as Event Viewer, Services and Computer Management |
| **Notifications (flag icon)** | Messages about tasks and configuration that still need to be completed |

> Active Directory tools, such as **Active Directory Users and Computers**, appear in the **Tools** menu only after the AD DS role is installed.

---

## 🔧 Open Server Manager

1. Connect to the VM with Remote Desktop and sign in with the local administrator account.
2. Server Manager opens automatically. If it does not, select **Start → Server Manager**.
3. Wait for the **Dashboard** to finish loading.

**Screenshot: Server Manager Dashboard:**

<img width="1920" height="1080" alt="Server Manager Dashboard on the Windows Server 2025 virtual machine" src="https://github.com/user-attachments/assets/b6d5ca15-841e-4a31-84f1-b4bdec91ae65" />

---

## ✅ Verification

Check the following in Server Manager:

| Check | Where | Expected Result |
|-------|-------|-----------------|
| Server Manager opens | After signing in | Dashboard is visible ✅ |
| Computer name | Local Server | `server2021` ✅ |
| Remote Desktop | Local Server | Enabled ✅ |
| Roles installed | Dashboard | None yet, because AD DS is installed in the next lab ✅ |

---

## 📝 Technical Notes

- **Before installing AD DS:** Set the server's private IP address to **Static** in the Azure network interface settings, so the Domain Controller's address does not change.
- **Server Manager is not the same as the Azure Portal:** The Azure Portal manages the VM as a cloud resource, for example Stop and Start. Server Manager manages Windows inside the VM, for example roles and local settings.
- **Privacy:** Crop the RDP connection bar at the top of the screen before publishing a screenshot, because it shows the server's address. Check that no IP address or username is visible.

---

## 💡 Next Step

→ [Install Active Directory Domain Services](./install-adds.md)
