
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


---

## 🔧 Part 1 - Failed Logon (Event ID 4625)

### Step 1 - Lock the Screen and Enter a Wrong Password

1. On the Windows 11 client, press **Windows key + L** to lock the screen.
2. Select Sam's account and enter a **wrong password**. Windows refuses the sign-in.


    **Screenshots: User Account Locked :**

   <img width="2268" height="3332" alt="Windows sign-in screen showing that the account is locked out" src="https://github.com/user-attachments/assets/c309ce41-ca4f-4c9d-9c4b-eca60fcdb87c" />


---
### Step 2 - Find Event ID 4625

The events are in the **client's** Security log, and reading it needs administrator rights.

1. Open **Event Viewer** as an administrator: press **Win + R**, type `eventvwr.msc`, and sign in with an administrator account if asked.
2. Expand **Windows Logs** and select **Security**.
3. Click **Filter Current Log...**, type `4625` in the **<All Event IDs>** box and click **OK**.
4. Double-click the entry from the time of the test and check the details:


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


**Screenshots: successful logon (Event ID 4624):**

<img width="1920" height="1080" alt="Screenshot (663)" src="https://github.com/user-attachments/assets/c4b073fa-fd99-4e2c-9289-725878e8e6b8" />








<img width="1920" height="1080" alt="Screenshot (664)" src="https://github.com/user-attachments/assets/3d455027-ea77-4d61-9fc2-148a02e4dc7b" />

> Clear the filter when you finish, or set it to `4624,4625` to see both events together.




---





## ✅ Verification

| Check | Where | Expected Result |
|-------|-------|-----------------|
| Failed attempt recorded | Client → Security log, filtered by 4625 | An **Audit Failure** entry for `Sam` ✅ |
| Successful logon recorded | Client → Security log, filtered by 4624 | An **Audit Success** entry for `Sam` ✅ |


---

## 💡 Next Step

→ [Event ID 4720 - User Account Created](./event-id-4720.md)




























#
