# 🖥️ Reset a User Password

[ Back to Overview] → [ADUC Overview and Organizational Unit Structure](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Active%20Directory/aduc-overview-and-organisation-unit-structure.md)

---

## 📋 Summary

Reset a domain user's forgotten password in Active Directory Users and Computers (ADUC), force the user to choose a new password at the next sign-in, and confirm that the user can sign in again.

---

## 💡 When is a Password Reset Used?

A password reset is one of the most common help desk tickets. The technician sets a temporary password, and the user replaces it with a private one at the next sign-in, so the technician never knows the final password.

| Setting | Value |
|---------|-------|
| **Tool** | Active Directory Users and Computers (ADUC) |
| **User account** | `JohnSmith` in the **IT** OU |
| **Password option** | User must change password at next logon |

---

## 🔧 Steps

### Step 1 - Verify the User's Identity

Before you reset a password, confirm that the caller is the account owner. Follow your organization's verification process, for example a callback to a registered number or a check by the user's manager.

### Step 2 - Find the User

On the Domain Controller, open **Server Manager → Tools → Active Directory Users and Computers**. Expand `seemaenterprise.co.in` and select the **IT** OU, or right-click the domain and select **Find** to search by name.

### Step 3 - Reset the Password

Right-click the user and select:

```text
Reset Password...
```

### Step 4 - Enter a Temporary Password

1. Enter a temporary password, and enter it again to confirm. It must meet the domain's password complexity rules.
2. Tick **User must change password at next logon**.
3. If the account is also locked, tick **Unlock the user's account**.
4. Click **OK**. ADUC confirms that the password was changed.

> Never show the temporary password in screenshots or in the repository.

**Screenshot: Reset Password window:**

<img width="1920" height="1080" alt="Reset Password window with the new password fields and User must change password at next logon selected" src="https://github.com/user-attachments/assets/1ddec7d5-38a3-420c-8690-4398e2341b9f" />

### Step 5 - Give the Temporary Password to the User Securely

Pass the temporary password through a secure channel, such as a verified phone call. Do not send it in an ordinary email or a chat message.




**Screenshot: password reset confirmed:**

<img width="1920" height="1080" alt="Confirmation that the password was changed and the user signing in on the client" src="https://github.com/user-attachments/assets/3958386f-6da6-4697-919b-27081de68719" />




---
### Step 6 - User Signs In and Sets a New Password

On the Windows 11 client, the user signs in with the temporary password, and Windows asks them to choose a new password.

```text
Username: SEEMAENTERPRISE\JohnSmith
Password: <temporary password>
```


---

## 💡 Next Step

→ [Unlock an Active Directory User Account](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Active%20Directory/unlock-account.md)
