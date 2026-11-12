# 🖥️ Enable and Disable User Accounts

[ Back to Overview] → [ADUC Overview and Organizational Unit Structure](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Active%20Directory/aduc-overview-and-organisation-unit-structure.md)

---

## 📋 Summary

Disable a domain user account in Active Directory Users and Computers (ADUC), confirm that the user can no longer sign in, then enable the account again and confirm that access is restored.

---

## 💡 Why Disable an Account?

Disabling an account blocks sign-in without deleting the account. The user's settings, group memberships and permissions stay in place, so the account can be enabled again later. This is used when an employee is on leave, leaves the company or when an account may be compromised.

| Setting | Value |
|---------|-------|
| **Tool** | Active Directory Users and Computers (ADUC) |
| **User account** | `SAM` |
| **Disabled account icon** | Down arrow on the user icon |

---

## 🔧 Steps

### Step 1 - Disable the Account

1. Open **Server Manager → Tools → Active Directory Users and Computers**.
2. Find the user, right-click it and select **Disable Account**.
3. ADUC shows a confirmation message. Click **OK**.

The user icon now shows a **down arrow**, which marks the account as disabled.

**Screenshots: account disabled:**

<img width="1920" height="1080" alt="ADUC context menu with Disable Account selected" src="https://github.com/user-attachments/assets/40eec28e-8e21-4f29-a4f9-2124ef4f89e7" />



### Step 2 - Test the Sign-In with the Disabled Account

On the Windows 11 client, try to sign in with the disabled account:

```text
Username: SEEMAENTERPRISE\JohnSmith
```

Windows blocks the sign-in with this message:

```text
Your account has been disabled. Please see your system administrator.
```

**Screenshot: sign-in Disabled:**

<img width="1920" height="1080" alt="ADUC showing the user icon with a down arrow after the account was disabled" src="https://github.com/user-attachments/assets/26826daf-7168-41ac-bdbd-af006977d85c" />

### Step 3 - Enable the Account

1. In ADUC, right-click the same user and select **Enable Account**.
2. ADUC shows a confirmation message. Click **OK**.

The user icon returns to normal, and the user can sign in again.

**Screenshot: account enabled:**





<img width="1920" height="1080" alt="Screenshot (602)" src="https://github.com/user-attachments/assets/98b1e58e-cda0-4691-ba17-8f556a2edece" />





<img width="1920" height="1080" alt="ADUC showing the user icon back to normal after the account was enabled" src="https://github.com/user-attachments/assets/19b15132-c133-4edd-87d1-035ce47ef6ff" />

---

## ✅ Verification

| Check | Where | Expected Result |
|-------|-------|-----------------|
| Account disabled | ADUC | User icon shows a down arrow ✅ |
| Sign-in blocked | Windows 11 client | "Your account has been disabled" message ✅ |
| Account enabled | ADUC | User icon is back to normal ✅ |
| Sign-in restored | Windows 11 client | The user signs in successfully ✅ |

---

## 💡 Next Step

→ Find a User Account in Active Directory](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Active%20Directory/find-user-in-ad.md
