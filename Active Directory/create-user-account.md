# 🖥️ Create a New User Account

[ Back to Overview] → [ADUC Overview and Organizational Unit Structure](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Active%20Directory/aduc-overview-and-organisation-unit-structure.md)

---

## 📋 Summary

Create a new domain user account in Active Directory Users and Computers (ADUC), place it in the **IT** Organizational Unit, and test the account by signing in on the Windows 11 client.

---

## 💡 What is a User Account?

A user account is an identity stored in Active Directory. It lets a person sign in to any domain-joined computer and receive the permissions and policies assigned to that account.

| Setting | Value |
|---------|-------|
| **Domain** | `seemaenterprise.co.in` |
| **Organizational Unit** | IT |
| **First name** | John |
| **Last name** | Smith |
| **User logon name** | `JohnSmith@seemaenterprise.co.in` |
| **Password option** | User must change password at next logon |

---

## 🔧 Steps

### Step 1 - Open the IT Organizational Unit

On the Domain Controller, open **Server Manager → Tools → Active Directory Users and Computers**, then expand `seemaenterprise.co.in` and select the **IT** OU.

### Step 2 - Start the New User Wizard

Right-click the **IT** OU and select:

```text
New → User
```

### Step 3 - Enter the User Details

| Field | Value |
|-------|-------|
| **First name** | John |
| **Last name** | Smith |
| **User logon name** | `JohnSmith` with the suffix `@seemaenterprise.co.in` |

Click **Next**.

**Screenshot: new user details:**

<img width="1920" height="1080" alt="New Object - User wizard with the name and user logon name entered" src="https://github.com/user-attachments/assets/ca016690-0f23-4b95-83b5-558604533b3c" />

### Step 4 - Set the Password

1. Enter a temporary password. It must meet the domain's password complexity rules.
2. Tick **User must change password at next logon**.
3. Click **Next**, then **Finish**.

> Never show the password in screenshots or in the repository.

**Screenshot: password options:**

<img width="1920" height="1080" alt="New Object - User wizard password page with User must change password at next logon selected" src="https://github.com/user-attachments/assets/fd53b87a-4af3-4b81-b395-f25518c17d6b" />










**Screenshot: user created**

<img width="1920" height="1080" alt="Active Directory Users and Computers showing John Smith in the IT OU" src="https://github.com/user-attachments/assets/e7531f20-71b2-4361-a5bc-12b52640b069" />





---








## 💡 Next Step

→ [Reset a User Password](./reset-user-password.md)
