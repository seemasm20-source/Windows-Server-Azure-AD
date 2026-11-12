
# 🖥️ Event Viewer Overview

[ Back to Overview] → [README.md](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/README.md)

---

## 📋 Summary

Event Viewer is the built-in Windows tool for reading the events that Windows, its services and its applications record. This section uses it in the `seemaenterprise.co.in` lab to investigate account lockouts, account creation, sign-ins, unexpected shutdowns and application crashes, on the Domain Controller, on the client and remotely.

---

## 💡 What is Event Viewer?

Windows records important activities and errors as **event logs**. IT administrators and support technicians use Event Viewer to find problems, investigate errors and understand what happened on a Windows computer or server.

Open it with:

```text
Win + R → eventvwr.msc → Enter
```

| Setting | Value |
|---------|-------|
| **Tool** | Event Viewer (`eventvwr.msc`) |
| **Domain** | `seemaenterprise.co.in` |
| **Domain Controller** | `server2021` |
| **Client** | Windows 11 client |
| **Test user** | `Sam` |

---

## 🗂️ Common Event Logs

| Log | What it records |
|-----|-----------------|
| **Application** | Events from applications and software |
| **System** | Windows system, driver and service events |
| **Security** | Security activity such as sign-ins, account changes and account lockouts. Reading it needs administrator rights |
| **Setup** | Windows installation and setup events |
| **Forwarded Events** | Events collected from other computers |

---

## 🔍 What an Event Contains

| Field | Meaning |
|-------|---------|
| **Event ID** | Identifies the specific event |
| **Level** | Information, Warning, Error or Critical |
| **Source** | The Windows component or service that wrote the event |
| **Date and Time** | When the event occurred |
| **Description** | Details about what happened |

> **Tip:** Right-click a log and select **Filter Current Log...**, then enter an Event ID in the **<All Event IDs>** box. This is much faster than scrolling through a large log.

---

## 🗂️ Event Viewer Labs in This Project

| Event ID | What it shows | Log | Where to look | Lab file |
|----------|---------------|-----|---------------|----------|
| **4740** | A user account was locked out | Security | Domain Controller | [Event ID 4740 - Account Locked Out](./event-id-4740.md) |
| **4720** | A user account was created | Security | Domain Controller | [Event ID 4720 - User Account Created](./event-id-4720.md) |
| **4625 and 4624** | A failed and a successful logon | Security | The computer the user signed in to | [Event ID 4625 and 4624 - Failed and Successful Logon](./event-id-4625-4624.md) |
| **41** | An unexpected shutdown or restart (Kernel-Power) | System | The affected computer | [Event ID 41 - Unexpected Shutdown](./event-id-41.md) |
| **1000** | An application crash | Application | The affected computer | [Event ID 1000 - Application Crash](./event-id-1000.md) |


> The Event ID 1000 file is an illustrative example, because an application crash could not be reproduced in the lab. It is labelled that way in the file.

---

## 🎯 Choosing the Right Event

| Ticket | Check this event | In this log |
|--------|------------------|-------------|
| "My account keeps getting locked" | 4740, then 4625 | Security, on the Domain Controller for 4740 |
| "Who created this account?" | 4720 | Security, on the Domain Controller |
| "Someone is trying to sign in to my account" | 4625 and 4624 | Security |
| "My computer restarted by itself" | 41, then 6008 and 1001 | System |
| "Outlook keeps crashing" | 1000 | Application |
| "A service stopped working" | 7034 | System |




---

## 🎯 IT Support Use

Event Viewer is commonly used to troubleshoot:

- Windows errors and crashes
- Application failures
- Login and authentication problems
- Account lockouts
- Service failures
- Driver issues
- Security-related events
- System startup and shutdown problems




---

## 💡 Next Step

→ [Windows Server on Azure Overview](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/README.md)# 🖥️ Event Viewer


