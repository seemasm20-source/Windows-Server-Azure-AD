

# 🖥️ Unlock a User Account

[ Back to Overview] → [README.md](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/README.md)

---

## 📋 Summary

Unlock a domain user account that was locked out after too many failed sign-in attempts, using the **Account** tab in Active Directory Users and Computers (ADUC).

---

## 💡 What is a Locked Account?

An account is **locked out** when the account lockout policy detects too many wrong password attempts in a short time. The lockout is temporary protection against password guessing, and the account stays locked until an administrator unlocks it or the lockout period ends.

| | Locked account | Disabled account |
|---|---|---|
| **Cause** | Too many wrong passwords | An administrator disabled it |
| **Icon in ADUC** | No change | Down arrow |
| **Fix** | Unlock account | Enable account |

| Setting | Value |
|---------|-------|
| **Tool** | Active Directory Users and Computers (ADUC) |
| **Location** | User **Properties → Account** tab |

---

## 🔧 Steps

### Step 1 - Open the User's Account Tab

1. Open **Server Manager → Tools → Active Directory Users and Computers**.
2. Find the user and right-click it.
3. Select **Properties**, then open the **Account** tab.

### Step 2 - Check the Lockout Status

If the account is locked, the **Account** tab shows an **Unlock account** checkbox with the message "This account is currently locked out on this Active Directory Domain Controller". The checkbox is **not ticked**.

If the account is not locked, the checkbox is greyed out.

**Screenshot: locked account:**

<img width="1920" height="1080" alt="User Properties Account tab with the Unlock account checkbox available for a locked account" src="https://github.com/user-attachments/assets/723a4e65-5ccc-4533-b0c4-3c42aa80fe64" />

### Step 3 - Unlock the Account

1. Tick **Unlock account**.
2. Click **OK**.

The account is unlocked, and the user can sign in again with their existing password. If the user also forgot the password, follow the Reset Password steps.

**Screenshot: account unlocked:**

<img width="1920" height="1080" alt="User Properties Account tab after the account was unlocked" src="https://github.com/user-attachments/assets/4a878238-f77c-4b0e-966e-fd989a040477" />

---

## ✅ Verification

| Check | Where | Expected Result |
|-------|-------|-----------------|
| Account unlocked | ADUC → Account tab | The **Unlock account** checkbox is greyed out ✅ |
| Sign-in | Windows 11 client | The user signs in successfully ✅ |

---

## 💡 Next Step

→ [Enable and Disable User Accounts](./enable-disable-user-accounts.md)




