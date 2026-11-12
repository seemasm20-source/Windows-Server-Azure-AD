# 🖥️ Event ID 41 - Unexpected Shutdown (Kernel-Power)

[ Back to Overview] → [Event Viewer – Overview](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Event%20Viewer/eventviewer-overview.md)

---

## 📋 Summary

Find Event ID 41 in the System log of Event Viewer, read what it says about the unexpected restart, and use the events around it to narrow down the cause.

---

## 💡 What is Event ID 41?

Event ID **41** (source **Kernel-Power**) is written to the **System** log when Windows starts after it was **not shut down cleanly**. The computer lost power, froze, crashed or was reset before Windows could close normally. The event is recorded at the next startup, not at the moment of the failure.

| Setting | Value |
|---------|-------|
| **Event ID** | 41 |
| **Source** | Kernel-Power |
| **Log** | Windows Logs → System |
| **Level** | Critical |
| **Tool** | Event Viewer (`eventvwr.msc`) |

### Fields to Read in the Event

| Field | What it shows |
|-------|---------------|
| **BugcheckCode** | `0` means Windows did not record a blue screen (BSOD) error. A non-zero value is a stop code from a crash |
| **SleepInProgress** | A non-zero value means the restart happened around a sleep or hibernate transition |
| **Date and Time** | When the system started again after the failure |

> A power cut, a hard reset or holding the power button shows **BugcheckCode: 0**. A BSOD normally shows a non-zero stop code, and also writes Event ID 1001 (BugCheck).

---

## 🔧 Steps

### Step 1 - Open Event Viewer

Press **Win + R**, type `eventvwr.msc` and press **Enter**.

### Step 2 - Find Event ID 41

1. Expand **Windows Logs** and select **System**.
2. Click **Filter Current Log...**, type `41` in the **<All Event IDs>** box and click **OK**.
3. Double-click the entry and read the **General** and **Details** tabs.

**Screenshots: Event ID 41:**

<img width="1920" height="1080" alt="System log filtered by Event ID 41 showing Kernel-Power events" src="https://github.com/user-attachments/assets/362fedec-676d-4198-af00-c3514657dcc2" />

<img width="1920" height="1080" alt="Event 41 details showing BugcheckCode and SleepInProgress" src="https://github.com/user-attachments/assets/4fc20fa9-3304-4749-b878-cec43071b2c8" />

---

### Step 4 - Investigate the Cause

Work from the simplest cause to the hardest:

1. **Power:** Check the power supply, battery and charger. A loose cable or a power cut causes this event.
2. **Updates and drivers:** Check Windows Update history and recently installed drivers, especially for graphics, storage and network.
3. **Overheating:** Check temperatures and dust, and check that the fans work.
4. **Hardware:** Check the disk health and memory, and look for hardware errors in the System log.
5. **System files:** If crashes continue, open an administrator Command Prompt and run `sfc /scannow` to check and repair protected system files.

```text
C:\> sfc /scannow
```





---

## ✅ Verification

| Check | Where | Expected Result |
|-------|-------|-----------------|
| Event found | System log, filtered by 41 | The entry is listed with **Level: Critical** ✅ |
| Cause investigated | Events around the shutdown, and the checks in Step 4 | A likely cause is identified ✅ |
| Normal restart | Restart the computer from the Start menu |  new Event 41 appears ✅ |
| Monitoring | Event Viewer over the next days | No new unexpected shutdown ✅ |

---

## 💡 Next Step

→ [Event IDs 4624 & 4625 – Successful and Failed Logon](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Event%20Viewer/event-id-4624-4625-successful-logon-failed-logon.md)






















































































