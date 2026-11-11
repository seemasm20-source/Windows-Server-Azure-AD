
# 🖥️ Event ID 4720 - User Account Created

[ Back to Overview] → [README.md](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/README.md)

---

## 📋 Summary

Create a new domain user account in Active Directory Users and Computers (ADUC), then find the matching Event ID 4720 in the Security log of the Domain Controller. The event shows who created the account and which account was created, which is useful for auditing and for investigating unexpected accounts.

---

## 💡 What is Event ID 4720?

Event ID **4720** is written to the **Security** log of a Domain Controller when a user account is created in Active Directory. It records the administrator who created the account and the name of the new account.

| Setting | Value |
|---------|-------|
| **Event ID** | 4720 (A user account was created) |
| **Log** | Windows Logs → Security |
| **Where it appears** | On the Domain Controller (`server2021`) |
| **Keyword** | Audit Success |
| **Tool** | Event Viewer (`eventvwr.msc`) |
| **New account** | `ziggy` |
| **Created by** | `Administrator` |

| Field in the event | What it shows |
|--------------------|---------------|
| **Subject → Account Name** | The administrator who created the account (`Administrator`) |
| **New Account → Account Name** | The account that was created (`ziggy`) |

---

## 🔧 Steps

### Step 1 - Create the User Account

1. Sign in to the Domain Controller `server2021`.
2. Open **Active Directory Users and Computers**: press **Win + R**, type `dsa.msc` and press **Enter**.
3. Right-click the target OU, for example **SALES**, and select **New → User**.
4. Enter the details for the new account:

| Field | Value |
|-------|-------|
| **First name / Full name** | `ziggy` |
| **User logon name** | `ziggy` |

5. Click **Next**, set a temporary password, and click **Finish**.





### Step 2 - Find the Event in Event Viewer

Creating the account writes Event ID 4720 to the Security log immediately.

1. Press **Win + R**, type `eventvwr.msc` and press **Enter**.
2. Expand **Windows Logs** and select **Security**.
3. Click **Filter Current Log...** in the right pane.
4. In the **<All Event IDs>** box, type `4720` and click **OK**.
5. Double-click the newest entry and read the description:

```text
A user account was created.

Subject:
    Account Name:   Administrator

New Account:
    Account Name:   ziggy
```

The event names the administrator as the creator and `ziggy` as the new account. The **Keywords** column shows **Audit Success**.

**Screenshot: Event ID 4720:**

<img width="1920" height="1080" alt="Security log filtered by Event ID 4720 showing the account ziggy created by Administrator" src="https://github.com/user-attachments/assets/01979d91-ad93-46c3-a94e-7c7c51bd39c6" />


<img width="1920" height="1080" alt="New Object - User wizard with the account name ziggy" src="https://github.com/user-attachments/assets/fcc49f1b-1d91-4e81-9fbe-ffb8bc25fce9" />

> Set the filter back to **All Event IDs** when you finish, or clear it, so the next search shows every event.

---

## 🛠️ Related Account Events

When an account is created, other events can follow. They show what else was done to the account:

| Event ID | Meaning |
|----------|---------|
| **4720** | A user account was created |
| **4722** | A user account was enabled |
| **4724** | An attempt was made to reset an account's password |
| **4725** | A user account was disabled |
| **4726** | A user account was deleted |
| **4740** | A user account was locked out |

---

## ✅ Verification

| Check | Where | Expected Result |
|-------|-------|-----------------|
| Account created | ADUC → target OU | `ziggy` is listed ✅ |
| Event recorded | Event Viewer → Security, filtered by 4720 | An entry for `ziggy` ✅ |
| Creator | Event details → Subject | `Administrator` ✅ |
| Status | Keywords column | Audit Success ✅ |

---

## 💡 Next Step

→ [Event ID 4740 - Account Locked Out](./event-id-4740.md)












