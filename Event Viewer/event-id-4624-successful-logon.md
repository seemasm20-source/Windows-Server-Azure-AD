













# 🖥️ Event ID 4625 and 4624 - Failed and Successful Logon

[ Back to Overview] → [README.md](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/README.md)

---

## 📋 Summary

Lock the Windows 11 client, enter a wrong password and then the correct one, and find both events in the client's Security log: Event ID 4625 for the failed logon and Event ID 4624 for the successful logon.

---

## 💡 What are Event IDs 4625 and 4624?

Windows records every sign-in attempt in the **Security** log. Event ID **4625** is a failed logon, and Event ID **4624** is a successful logon. Together they show who signed in, when, how and from where, so they are the first events to check when investigating sign-in problems or suspicious access.

| Setting | Value |
|---------|-------|
| **Events** | 4625 (failed logon) and 4624 (successful logon) |
| **Log** | Windows Logs → Security, on the **client** computer |
| **Keywords** | Audit Failure (4625) and Audit Success (4624) |
| **Tool** | Event Viewer (`eventvwr.msc`) |
| **Client** | Windows 11 client |
| **Test user** | `Sam` |

### Logon Types

| Logon Type | Name | Meaning |
|:----------:|------|---------|
| **2** | Interactive | Signing in at the sign-in screen, at the keyboard |
| **3** | Network | Connecting to a shared folder over the network |
| **7** | Unlock | Unlocking a locked workstation |
| **10** | RemoteInteractive | Signing in through Remote Desktop |

> In this lab the screen was locked and then unlocked, so the events show **Logon Type 7 (Unlock)**. Check your screenshots, because a sign-in from the sign-in screen shows Type 2.

---

## 🔧 Part 1 - Failed Logon (Event ID 4625)

### Step 1 - Lock the Screen and Enter a Wrong Password

1. On the Windows 11 client, press **Windows key + L** to lock the screen.
2. Select Sam's account and enter a **wrong password**. Windows refuses the sign-in.

### Step 2 - Find Event ID 4625

The events are in the **client's** Security log, and reading it needs administrator rights.

1. Open **Event Viewer** as an administrator: press **Win + R**, type `eventvwr.msc`, and sign in with an administrator account if asked.
2. Expand **Windows Logs** and select **Security**.
3. Click **Filter Current Log...**, type `4625` in the **<All Event IDs>** box and click **OK**.
4. Double-click the entry from the time of the test and check the details:

```text
Audit Failure
Account For Which Logon Failed:   Account Name: Sam
Logon Type: 7
```

**Screenshots: failed logon (Event ID 4625):**

<img width="1920" height="1080" alt="Security log filtered by Event ID 4625 showing an Audit Failure entry" src="https://github.com/user-attachments/assets/a3e9501d-5868-4692-9385-f9665798a85c" />

<img width="1920" height="1080" alt="Event 4625 details showing the account name Sam and the logon type" src="https://github.com/user-attachments/assets/ed99412a-254c-4152-9e40-5c14cd98f464" />

---

## 🔧 Part 2 - Successful Logon (Event ID 4624)

### Step 1 - Enter the Correct Password

On the same lock screen, enter Sam's **correct password**. The screen unlocks and the desktop opens.

### Step 2 - Find Event ID 4624

1. In the **Security** log, click **Filter Current Log...**, type `4624` and click **OK**.
2. Double-click the entry from the time of the unlock and check the details:

```text
Audit Success
New Logon:   Account Name: Sam
Logon Type: 7
```

**Screenshots: successful logon (Event ID 4624):**

<!-- Add the screenshot of the Security log filtered by 4624 here -->

<!-- Add the screenshot of the Event 4624 details here -->

> Clear the filter when you finish, or set it to `4624,4625` to see both events together.

---

## 🛠️ Related Logon Events

| Event ID | Meaning |
|----------|---------|
| **4624** | An account was successfully logged on |
| **4625** | An account failed to log on |
| **4800** | The workstation was locked |
| **4801** | The workstation was unlocked |
| **4740** | A user account was locked out (on the Domain Controller) |

---

## ✅ Verification

| Check | Where | Expected Result |
|-------|-------|-----------------|
| Failed attempt recorded | Client → Security log, filtered by 4625 | An **Audit Failure** entry for `Sam` ✅ |
| Successful logon recorded | Client → Security log, filtered by 4624 | An **Audit Success** entry for `Sam` ✅ |
| Same logon type | Both events | **Logon Type 7** for an unlock ✅ |

---

## 💡 Next Step

→ [Event ID 4720 - User Account Created](./event-id-4720.md)




























# 🖥️ Event ID 4624 - Successful Logon

[ Back to Overview] → [README.md](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/README.md)

---

## 📋 Summary

Lock the Windows 11 client, enter a wrong password and then the correct one, and find the matching events in the client's Security log: Event ID 4625 for the failed attempt and Event ID 4624 for the successful logon.

---

## 💡 What is Event ID 4624?

Event ID **4624** is written to the **Security** log when an account logs on successfully. Event ID **4625** is written when a logon fails. Together they show who signed in, when, how and from where, so they are the first events to check when investigating sign-in problems or suspicious access.

| Setting | Value |
|---------|-------|
| **Events** | 4624 (successful logon) and 4625 (failed logon) |
| **Log** | Windows Logs → Security, on the **client** computer |
| **Keywords** | Audit Success (4624) and Audit Failure (4625) |
| **Tool** | Event Viewer (`eventvwr.msc`) |
| **Client** | Windows 11 client |
| **Test user** | `Sam` |

### Logon Types

Every 4624 and 4625 event has a **Logon Type** that shows how the user signed in:

| Logon Type | Name | Meaning |
|:----------:|------|---------|
| **2** | Interactive | Signing in at the sign-in screen, at the keyboard |
| **3** | Network | Connecting to a shared folder over the network |
| **7** | Unlock | Unlocking a locked workstation |
| **10** | RemoteInteractive | Signing in through Remote Desktop |

> In this lab the screen was **locked and then unlocked**, so the successful logon shows **Logon Type 7 (Unlock)**. Logon Type 2 appears when a user signs in from the sign-in screen after signing out or restarting.

---

## 🔧 Steps

### Step 1 - Lock the Screen

On the Windows 11 client, press **Windows key + L** to lock the screen.

### Step 2 - Enter a Wrong Password

Select Sam's account and enter a **wrong password**. Windows refuses the sign-in. The attempt is recorded as **Event ID 4625** with **Audit Failure**.

### Step 3 - Enter the Correct Password

Enter Sam's **correct password**. The screen unlocks and the desktop opens. The sign-in is recorded as **Event ID 4624** with **Audit Success**.

### Step 4 - Find the Events in Event Viewer

The events are in the **client's** Security log, and reading the Security log needs administrator rights.

1. Open **Event Viewer** as an administrator: press **Win + R**, type `eventvwr.msc` and sign in with an administrator account if asked.
2. Expand **Windows Logs** and select **Security**.
3. Click **Filter Current Log...** and, in the **<All Event IDs>** box, type `4624,4625`, then click **OK**.
4. Find the entries from the time of the test and double-click each one.

For the failed attempt (4625), check:

```text
Audit Failure
Account For Which Logon Failed:   Account Name: Sam
Logon Type: 7
```

For the successful logon (4624), check:

```text
Audit Success
New Logon:   Account Name: Sam
Logon Type: 7
```

**Screenshots: events in the Security log:**

<img width="1920" height="1080" alt="Security log filtered by Event IDs 4624 and 4625 showing a failure and a success" src="https://github.com/user-attachments/assets/a3e9501d-5868-4692-9385-f9665798a85c" />

<img width="1920" height="1080" alt="Event 4624 details showing the account name Sam and the logon type" src="https://github.com/user-attachments/assets/ed99412a-254c-4152-9e40-5c14cd98f464" />

> Clear the filter when you finish, so the next search shows every event.

---

## 🛠️ Related Logon Events

| Event ID | Meaning |
|----------|---------|
| **4624** | An account was successfully logged on |
| **4625** | An account failed to log on |
| **4800** | The workstation was locked |
| **4801** | The workstation was unlocked |
| **4740** | A user account was locked out (on the Domain Controller) |

---

## ✅ Verification

| Check | Where | Expected Result |
|-------|-------|-----------------|
| Failed attempt recorded | Client → Security log, filtered by 4625 | An **Audit Failure** entry for `Sam` ✅ |
| Successful logon recorded | Client → Security log, filtered by 4624 | An **Audit Success** entry for `Sam`, with **Logon Type 7** ✅ |

---

## 💡 Next Step

→ [Event ID 4720 - User Account Created](./event-id-4720.md)










































## Event ID 4624 - Successful Logon

This logs when a user physically types their password to unlock their desk monitor.

1. Go to your Windows 11 client machine.

2. Press Windows Key + L to lock the screen.

3. Log back in as Sam using his correct password.

4. The Result: This action instantly writes an Event ID 4624 to the local client's Security log with Logon Type: 2.

   __Note : For some reason, I am unable to see security logs in client machine even though I run Eventviewer as Administrator.__




<img width="1920" height="1080" alt="Screenshot (663)" src="https://github.com/user-attachments/assets/c4b073fa-fd99-4e2c-9289-725878e8e6b8" />







































































































<img width="1920" height="1080" alt="Screenshot (664)" src="https://github.com/user-attachments/assets/3d455027-ea77-4d61-9fc2-148a02e4dc7b" />










