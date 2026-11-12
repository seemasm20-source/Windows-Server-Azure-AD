# 🖥️ Event ID 1000 - Application Crash

[ Back to Overview] → [README.md](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/README.md)

---

> **Lab Note:** An application crash could not be reproduced in the lab. The event below is an illustrative example of what Event ID 1000 looks like and how a technician reads it. Actual values vary with the application and the fault.

## 📋 Summary

A user reports that an application keeps crashing. Event ID 1000 in the **Application** log shows which program crashed, which module caused it and the error code. This file shows how to read the event and how to use it to fix the problem, using Outlook as an example.

---

## 💡 What is Event ID 1000?

Event ID **1000** (source **Application Error**) is written to the **Application** log when a program crashes. It names the faulting application and the faulting module (the file that was running when it failed), which tells a technician where to start.

| Setting | Value |
|---------|-------|
| **Event ID** | 1000 |
| **Source** | Application Error |
| **Log** | Windows Logs → Application |
| **Level** | Error |
| **Tool** | Event Viewer (`eventvwr.msc`) |

### Example Event

```text
Faulting application name: OUTLOOK.EXE
Faulting module name:      mso.dll
Exception code:            0xc0000005
```

| Field | What it shows |
|-------|---------------|
| **Faulting application name** | The program that crashed (`OUTLOOK.EXE`) |
| **Faulting module name** | The file inside the program that failed. Here `mso.dll`, a shared Microsoft Office component. It can also be an add-in or a driver file |
| **Exception code** | The kind of error. `0xc0000005` is an **access violation**: the program tried to use memory it was not allowed to use |
| **Fault offset, process ID and paths** | Extra details for deeper analysis |

> The faulting module is a **clue, not always the cause**. A damaged Office installation, a faulty add-in or a corrupt profile can all appear in the same event, so check the module name together with the steps below.

---

## 🔧 Steps

### Step 1 - Find the Event

1. Press **Win + R**, type `eventvwr.msc` and press **Enter**.
2. Expand **Windows Logs** and select **Application**.
3. Click **Filter Current Log...**, type `1000` in the **<All Event IDs>** box and click **OK**.
4. Double-click the entry that matches the time of the crash and read the **General** tab.

### Step 2 - Identify the Fault

Read the faulting application, the faulting module and the exception code, and compare them with the user's ticket.

| Ticket | Faulting application | Faulting module | Exception code |
|--------|----------------------|-----------------|----------------|
| Outlook keeps crashing | `OUTLOOK.EXE` | `mso.dll` | `0xc0000005` |


### Step 3 - Fix the Problem

Work from the simplest fix to the hardest:

1. **Start Outlook in safe mode:** press **Win + R**, type `outlook.exe /safe` and press **Enter**. If it works, an add-in is the likely cause.
2. **Disable add-ins:** open **File → Options → Add-ins**, and turn off add-ins one at a time.
3. **Update Office:** install the latest updates, because a bug fix may already exist.
4. **Repair Office:** open **Settings → Apps → Installed apps**, select **Microsoft 365** (or Office), then **Modify**, and choose **Quick Repair**. If the crash continues, choose **Online Repair**.
5. **Create a new Outlook profile:** if the problem stays, a damaged profile may be the cause.

---

## 🛠️ Common Causes

| Cause | Typical sign |
|-------|--------------|
| **Faulty add-in** | Outlook works in safe mode, and the faulting module is an add-in file |
| **Damaged Office installation** | A Microsoft module such as `mso.dll` is named, and safe mode also fails |
| **Corrupt profile or data file** | Crashes happen at a certain action, such as opening a mailbox |
| **Outdated software** | A known bug that an update fixes |

---

## ✅ Verification

| Check | Where | Expected Result |
|-------|-------|-----------------|
| Cause identified | Event 1000 details | Faulting application and module are known ✅ |
| Fix applied | Safe mode, add-ins, update or repair | A fix from Step 3 is applied ✅ |
| Application stable | Use Outlook normally for a period of time | No crash, and no new Event ID 1000 for `OUTLOOK.EXE` ✅ |

---

## 💡 Next Step

→ [Event ID 41 - Unexpected Shutdown](./event-id-41.md)
