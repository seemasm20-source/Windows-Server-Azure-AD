
# 🖥️ Remote Event Viewer

[ Back to Overview] → [README.md](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/README.md)


---

## 📋 Summary

Use Event Viewer to read the event logs of another Windows computer, without opening a full Remote Desktop session. In this lab the console connects to the Domain Controller `server2021` and reviews its System and Application logs.

---

## 💡 What is Remote Event Viewer?

Event Viewer (`eventvwr.msc`) shows the events that Windows and its applications record. It can connect to another computer, so a technician can investigate problems on it without taking over its desktop. It helps with:

- Application crashes
- Unexpected shutdowns and restarts
- System errors, such as driver problems and service failures
- Authentication issues, such as failed sign-ins

| Setting | Value |
|---------|-------|
| **Platform** | Microsoft Azure |
| **Admin machine** | Windows 11 client VM, signed in with a domain administrator account |
| **Target machine** | `server2021` (Windows Server) |
| **Tool** | Event Viewer (`eventvwr.msc`) |
| **Logs** | Windows Logs: System, Application and Security |

> Event Viewer can also be opened from [Remote Computer Management](./remote-computer-management.md). This file covers the log review in more detail.

---

## 🔧 Steps

### Step 1 - Open Event Viewer

1. Sign in to the Windows machine used for administration.
2. Press **Win + R**, type `eventvwr.msc` and press **Enter**.

### Step 2 - Connect to the Remote Computer

1. In Event Viewer, right-click **Event Viewer (Local)**.
2. Select **Connect to Another Computer...**
3. Select **Another computer** and enter the target's hostname or IP address:

```text
server2021
```

4. Click **OK** and wait for the remote logs to load. The tree now shows **Event Viewer (server2021)**.

### Step 3 - Review the Logs

1. Expand **Windows Logs**.
2. Select **System** or **Application** to read the events of the remote computer.
3. Double-click an event and review its **Source**, **Event ID**, **Date and Time**, **Level** and **General** description, and the **Details** tab.

**Screenshot: remote Event Viewer:**

<img width="2147" height="1994" alt="Event Viewer connected to server2021 showing the System log" src="https://github.com/user-attachments/assets/80495adf-9f59-4bb6-a652-228ec5bcee39" />

> To find a problem faster, right-click the log, select **Filter Current Log...**, and tick **Critical**, **Error** and **Warning**.



<img width="1920" height="1080" alt="Screenshot (667)" src="https://github.com/user-attachments/assets/f7f6e82b-b87c-442e-9d4a-89cf850dd6fd" />


---

## 🛠️ What to Look For

| Problem | Log | Examples |
|---------|-----|----------|
| **Unexpected shutdown or restart** | System | Event ID **41** (Kernel-Power) and **6008** (the previous shutdown was unexpected) |
| **Service failure** | System | Event ID **7034** (a service terminated unexpectedly) |
| **Application crash** | Application | Event ID **1000** (Application Error) |
| **Failed sign-in** | Security | Event ID **4625** (an account failed to log on). Audit events must be enabled, and your account needs permission to read the Security log |

---

## 🔧 Troubleshooting Remote Event Viewer

| Symptom | Likely cause | What to check |
|---------|--------------|---------------|
| **Cannot connect to the remote computer** | Wrong name, DNS problem, no network path or a firewall block | Ping the target, check the hostname or IP, and check the firewall |
| **Access denied** | The account has no permission to read the target's logs | Sign in as an administrator, or add the account to the target's **Event Log Readers** group |
| **The RPC server is unavailable** | The remote Event Log firewall rule is off | On the target, enable the inbound rule **Remote Event Log Management** |
| **Security log is empty or blocked** | Auditing is off, or the account lacks permission | Check the audit policy, and use an administrator account |



---


## 💡 Next Step

→ [UNC Path Access – Windows Network Sharing](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Remote%20Support%20Tools/unc-path-access.md)














































