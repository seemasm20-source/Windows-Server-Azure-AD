

# 🖥️ Remote Computer Management

[ Back to Overview] → [README.md](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/README.md)

---

## 📋 Summary

Use the Computer Management console to manage another Windows computer from an administrator's machine, without opening a full Remote Desktop session. In this lab it is used to connect to the Domain Controller `server2021` and check its management tools.

---

## 💡 What is Remote Computer Management?

Computer Management (`compmgmt.msc`) is an administrative console. It can connect to another Windows computer, so a technician can investigate or manage it without taking over its desktop. Depending on permissions and configuration, it can be used to:

- View Event Viewer logs
- Manage services
- Check shared folders and open sessions
- Check disks
- Perform other administrative tasks

| Setting | Value |
|---------|-------|
| **Platform** | Microsoft Azure |
| **Admin machine** | Windows 11 client, signed in with a domain administrator account |
| **Target machine** | `server2021` (Windows Server) |
| **Tool** | Computer Management (`compmgmt.msc`) |

> **Note:** Remote Computer Management is an administrative console, not a remote-control application. It lets you investigate or manage another computer without taking over its desktop. If you need to see and control the desktop, use [Remote Desktop](./rdp.md).

---

## 🔧 Steps

### Step 1 - Open Computer Management

1. Sign in to the Windows machine used for administration.
2. Press **Win + R**, type `compmgmt.msc` and press **Enter**.

**Screenshot: Connecting to Computer Management console:**

<img width="1920" height="1080" alt="Computer Management console opened with compmgmt.msc" src="https://github.com/user-attachments/assets/b7c44da7-afad-4b50-9c34-b0f4240b2b75" />

### Step 2 - Connect to Another Computer

1. In the Computer Management console, right-click **Computer Management (Local)**.
2. Select **Connect to another computer...**
3. Select **Another computer** and enter the target's hostname or IP address:

```text
server2021
```

4. Click **OK** and wait for the remote console to load. The tree changes from **Computer Management (Local)** to **Computer Management (server2021)**.

**Screenshots: connecting to the target:**



<img width="1920" height="1080" alt="Select Computer window with the target server2021 entered" src="https://github.com/user-attachments/assets/27ccba73-670a-4b40-9ec8-e37cbfbf8a7c" />





<img width="1920" height="1080" alt="Computer Management connected to server2021 with Event Viewer expanded" src="https://github.com/user-attachments/assets/35fedf20-d734-40e6-85dd-c79c7840fbcc" />

<img width="1920" height="1080" alt="Computer Management connected to server2021 showing the Services list" src="https://github.com/user-attachments/assets/b8bbd93d-5cf9-4618-ada5-6af7cfe8bd84" />


### Step 3 - Check the Available Tools

Expand the sections in the left pane and check which tools you can open on the remote computer:

| Section | Tool | What you can do remotely |
|---------|------|--------------------------|
| **System Tools** | Event Viewer | Read the event logs of the remote computer |
| **System Tools** | Shared Folders | See shares, open sessions and open files |
| **System Tools** | Device Manager | View devices only. Changes are not possible remotely |
| **Storage** | Disk Management | View disks and volumes |
| **Services and Applications** | Services | Start, stop and restart services |

> **Local Users and Groups** is not available on a Domain Controller. Use Active Directory Users and Computers instead.

**Screenshots: remote management tools:**



<img width="1920" height="1080" alt="Right-click menu on Computer Management Local with Connect to another computer" src="https://github.com/user-attachments/assets/d3a66ad7-155b-40b1-b088-ad025741bf06" />  



---

## 🛠️ Troubleshooting Remote Management

| Symptom | Likely cause | What to check |
|---------|--------------|---------------|
| **Cannot connect to the remote computer** (network path not found) | Wrong name or address, no network path, or a firewall block | Ping the target, check the hostname or IP, and check the firewall on the target |
| **Access denied** | The account is not an administrator on the target | Sign in with a domain administrator account, or add the account to the target's local **Administrators** group |
| **Some tools show an error or stay empty** | The remote management firewall rules are off | On the target, enable the inbound rules for remote management, such as **Remote Event Log Management**, **Remote Service Management** and **Windows Management Instrumentation (WMI-In)** |
| **Hostname not resolving** | DNS problem | Use the IP address, then check the DNS server on the admin machine |




---

## 💡 Next Step

→ [Remote Desktop Protocol (RDP) – Troubleshooting Guide](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Remote%20Support%20Tools/remote-desktop-protocol.md)



























