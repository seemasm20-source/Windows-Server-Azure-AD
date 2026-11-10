
# 🖥️ Password and Lockout Policy

[ Back to Overview] → [Group Policy (GPO) Overview and Linking](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Group%20Policy%20(GPO)/gpo-overview-and-linking.md)

---

## 📋 Summary

Use the Default Domain Policy to set a password policy (length, complexity, age and history) and an account lockout policy (threshold, duration and reset counter) for all domain users. Then test the lockout on the Windows 11 client.

---

## 💡 What are Password and Lockout Policies?

A password policy sets the rules for passwords, so weak passwords are not accepted. A lockout policy locks an account after too many wrong passwords, which protects against password guessing (brute force).

| Setting | Value |
|---------|-------|
| **Tool** | Group Policy Management (`gpmc.msc`) on the Domain Controller |
| **GPO** | Default Domain Policy, linked to `seemaenterprise.co.in` |
| **Policy path** | Computer Configuration → Policies → Windows Settings → Security Settings → Account Policies |

> Password and lockout settings for **domain accounts** only work when they are in a GPO linked at the **domain root**, such as the Default Domain Policy. A policy linked to an OU does not change the password rules for domain users.

---

## 🔧 Steps

### Step 1 - Open the Default Domain Policy

1. On the Domain Controller, open **Group Policy Management** (`gpmc.msc`).
2. Expand **Forest → Domains** and select your domain, `seemaenterprise.co.in`.
3. The **Default Domain Policy** is linked here.
4. Right-click **Default Domain Policy** and select **Edit**. This opens the Group Policy Management Editor.

**Screenshots: opening the Default Domain Policy:**

<img width="1920" height="1080" alt="Group Policy Management with the domain and the Default Domain Policy" src="https://github.com/user-attachments/assets/27a2d04c-5053-4129-b5bb-2d13674740e5" />

<img width="1920" height="1080" alt="Default Domain Policy opened in the Group Policy Management Editor" src="https://github.com/user-attachments/assets/b91b826e-f72d-47b6-88ac-8a37a17c1302" />

### Step 2 - Configure the Password Policy

In the editor, go to:

```text
Computer Configuration → Policies → Windows Settings → Security Settings → Account Policies → Password Policy
```

Double-click each setting in the right pane and set the following values:

| Setting | Value | Purpose |
|---------|-------|---------|
| **Minimum password length** | 12 characters | Longer passwords are harder to guess |
| **Password must meet complexity requirements** | Enabled | Requires a mix of character types |
| **Maximum password age** | 90 days | Passwords expire and must be changed. A value of `0` means they never expire |
| **Enforce password history** | 24 passwords remembered | Stops users from reusing old passwords |

> **Complexity** means the password cannot contain the user's name and must use characters from at least three of these groups: uppercase, lowercase, numbers and symbols.

**Screenshots: password policy settings:**

<img width="1920" height="1080" alt="Password Policy settings in the Group Policy Management Editor" src="https://github.com/user-attachments/assets/ababa622-0d79-4752-9e20-4c0c667b7423" />

<img width="1920" height="1080" alt="Minimum password length set to 12 characters" src="https://github.com/user-attachments/assets/009c4b87-e4d3-472d-967c-aeb4cf6fd39b" />

<img width="1920" height="1080" alt="Password must meet complexity requirements set to Enabled" src="https://github.com/user-attachments/assets/d634644b-c207-46b5-bd52-aa1074d3b1c9" />

<img width="1920" height="1080" alt="Maximum password age and Enforce password history settings" src="https://github.com/user-attachments/assets/9d6f3a6d-4048-47bc-855f-ddba8020841e" />

> These rules apply when a password is **changed or reset**. Existing passwords stay valid until their next change. Temporary passwords set in ADUC must also meet the new length and complexity.

### Step 3 - Configure the Account Lockout Policy

In the left pane, select **Account Lockout Policy**, directly below **Password Policy**, and configure three connected settings:

| Setting | Value | Meaning |
|---------|-------|---------|
| **Account lockout threshold** | 5 invalid logon attempts | The account locks after 5 wrong passwords |
| **Account lockout duration** | 30 minutes | How long the account stays locked before it unlocks itself |
| **Reset account lockout counter after** | 30 minutes | How long after a failed attempt the failed-attempt count returns to zero |

> When you set the threshold and click **Apply**, Windows suggests default values for the other two settings, 30 minutes each. Click **OK** to accept them, or change them yourself. The reset counter value must be **less than or equal to** the lockout duration.

**Screenshots: account lockout settings:**

<img width="1920" height="1080" alt="Account Lockout Policy list in the Group Policy Management Editor" src="https://github.com/user-attachments/assets/71297e6c-bd38-4b6d-bdd1-2c9a0d4484fb" />

<img width="1920" height="1080" alt="Account lockout threshold set to 5 invalid logon attempts" src="https://github.com/user-attachments/assets/072fa9ca-3d5d-4482-9c64-e3f25835c4c6" />

<img width="1920" height="1080" alt="Suggested values for lockout duration and reset counter" src="https://github.com/user-attachments/assets/47a1892f-d225-4f3a-a831-e309cc568bab" />

### Step 4 - Apply and Test the Policy

1. On the Domain Controller and on the Windows 11 client, open **Command Prompt as administrator** and run:

```text
C:\> gpupdate /force
```

2. On the client, sign out. At the sign-in screen, enter a **wrong password 5 times in a row** for a test user, for example Sam.
3. On the sixth attempt, Windows blocks the sign-in with a message that the account is locked out, for example:

```text
The referenced account is currently locked out and may not be logged on to.
```

4. To unlock the account before the 30 minutes end, use ADUC. See [Unlock an Active Directory User Account](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Active%20Directory/unlock-account.md)

**Screenshots: lockout test:**

<img width="2268" height="2910" alt="Wrong password entered at the Windows 11 sign-in screen" src="https://github.com/user-attachments/assets/31cb0af4-f286-4557-bcfb-f22ca63e6d4a" />

<img width="2268" height="3332" alt="Windows sign-in screen showing that the account is locked out" src="https://github.com/user-attachments/assets/c309ce41-ca4f-4c9d-9c4b-eca60fcdb87c" />

<img width="1920" height="1080" alt="ADUC Account tab for the user showing the account as locked out" src="https://github.com/user-attachments/assets/b5dc0d5f-c9e0-4452-bc36-e3c3976854ba" />

---

## ✅ Verification

| Check | Where | Expected Result |
|-------|-------|-----------------|
| Password policy set | Default Domain Policy → Password Policy | Length 12, complexity Enabled, age 90 days, history 24 ✅ |
| Lockout policy set | Default Domain Policy → Account Lockout Policy | Threshold 5, duration 30 minutes, reset 30 minutes ✅ |
| Policy refreshed | `gpupdate /force` | Computer and User policy updated successfully ✅ |
| Lockout works | Client sign-in | The account locks after 5 wrong passwords ✅ |
| Account unlocked | ADUC → user Properties → Account | The account is unlocked and the user can sign in ✅ |

---

## 💡 Next Step

→ [Restrict Control Panel Access Using Group Policy (GPO)](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Group%20Policy%20(GPO)/restrict-control-panel.md)







































