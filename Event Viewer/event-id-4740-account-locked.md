# 🖥️ Event ID 4740 - Account Locked Out

[ Back to Overview] → [Event Viewer – Overview](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Event%20Viewer/eventviewer-overview.md)

---

## 📋 Summary

Lock a domain user account by entering wrong passwords on the Windows 11 client, find the lockout event (Event ID 4740) in the Event Viewer on the Domain Controller, identify which account and which computer caused it, then unlock the account in Active Directory Users and Computers (ADUC).

---

## 💡 What is Event ID 4740?

Event ID **4740** is written to the **Security** log of the Domain Controller when a user account is locked out. It tells a technician which account was locked and which computer the failed sign-ins came from. This is the first thing to check when a user keeps getting locked out.

| Setting | Value |
|---------|-------|
| **Event ID** | 4740 (A user account was locked out) |
| **Log** | Windows Logs → Security, on the Domain Controller |
| **Tool** | Event Viewer (`eventvwr.msc`) |
| **Domain Controller** | `server2021` |
| **Client** | Windows 11 client |
| **Test user** | `Sam` |
| **Lockout threshold** | 5 invalid logon attempts, set in the [Password and Lockout Policy](./password-lockout-policy.md) file |

| Field in the event | What it shows |
|--------------------|---------------|
| **Account That Was Locked Out → Account Name** | The user whose account was locked (`Sam`) |
| **Additional Information → Caller Computer Name** | The computer the failed sign-ins came from |

---

## 🔧 Steps

### Step 1 - Trigger the Lockout on the Client

1. Go to the Windows 11 client. If you are signed in, press **Windows key + L** to lock the screen.
2. Select Sam's account and enter a **wrong password**.
3. Press **Enter**. Repeat until the number of failed attempts reaches the lockout threshold (5 in this lab).
4. On the next attempt, Windows blocks the sign-in with this message:

```text
The referenced account is currently locked out and may not be logged on to.
```

**Screenshot: account locked out at the sign-in screen:**

<img width="2268" height="3332" alt="Windows sign-in screen showing that the account is locked out" src="https://github.com/user-attachments/assets/c309ce41-ca4f-4c9d-9c4b-eca60fcdb87c" />

### Step 2 - Find the Lockout Event on the Server

1. Sign in to `server2021`.
2. Press **Win + R**, type `eventvwr.msc` and press **Enter**.
3. In the left pane, expand **Windows Logs** and select **Security**.
4. In the right pane, click **Filter Current Log...**
5. In the **<All Event IDs>** box, type `4740` and click **OK**.
6. An entry appears at the time of the lockout. Double-click it and read the description:

```text
Account That Was Locked Out:
    Account Name:         Sam

Additional Information:
    Caller Computer Name: <client computer name>
```

The caller computer name shows which machine the wrong passwords came from, here the Windows 11 client.

> The Security log can be large, so the filter by Event ID saves time. The event appears on the Domain Controller, not on the client.

**Screenshots: finding the event:**
<img width="1920" height="1080" alt="Screenshot (661)" src="https://github.com/user-attachments/assets/68356d9a-2a39-4202-81c2-f310894278af" />



<img width="1920" height="1080" alt="Sam's Account tab in ADUC with the Unlock account option" src="https://github.com/user-attachments/assets/94ec00b2-229e-48b9-92b4-f5c445ee7701" />

### Step 3 - Unlock the Account in ADUC

1. On the server, open **Active Directory Users and Computers**.
2. Open the **IT** OU, where Sam's account is.
3. Right-click **Sam** and select **Properties**.
4. Open the **Account** tab.
5. The account shows as locked out. Tick **Unlock account**.
6. Click **Apply**, then **OK**.

**Screenshot: unlocking the account:**



<img width="1920" height="1080" alt="Event Viewer Security log filtered by Event ID 4740" src="https://github.com/user-attachments/assets/b5dc0d5f-c9e0-4452-bc36-e3c3976854ba" />



### Step 4 - Verify on the Client

1. Go back to the Windows 11 client.
2. Enter Sam's **correct password**.
3. The sign-in succeeds and Sam's desktop opens, which confirms that the unlock worked.

---

## ✅ Verification

| Check | Where | Expected Result |
|-------|-------|-----------------|
| Account locked | Client sign-in screen | "The referenced account is currently locked out" message ✅ |
| Event recorded | Server → Event Viewer → Security, filtered by 4740 | An entry for Sam with the caller computer name ✅ |
| Account unlocked | ADUC → Account tab | The account is no longer locked ✅ |
| Sign-in restored | Client | Sam signs in with the correct password ✅ |

---


## 💡 Next Step

→ [Event ID 4720 – User Account Created](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Event%20Viewer/event-id-4720-user-created.md)





























































