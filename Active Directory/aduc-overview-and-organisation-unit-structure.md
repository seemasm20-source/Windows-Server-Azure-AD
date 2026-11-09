# 🏢 Active Directory Users and Computers (ADUC) and OU Structure

[ Back to Overview] → [README.md](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/README.md)

---

## 📋 Summary

This lab builds a small Active Directory environment on Microsoft Azure: a Windows Server 2025 VM promoted to a Domain Controller for `seemaenterprise.co.in`, and a Windows 11 Pro client joined to the domain. **Active Directory Users and Computers (ADUC)** is the console used to manage the domain's users, computers and groups. This file explains ADUC and builds the Organizational Unit (OU) structure for the company's departments.

---

## 💡 What is ADUC?

ADUC is a management console for the objects in an Active Directory domain:

- User accounts
- Computer accounts
- Security groups
- Organizational Units (OUs)
- Domain Controller objects

Open it from the Domain Controller:

```text
Server Manager → Tools → Active Directory Users and Computers
```

> The **Active Directory Users and Computers** entry appears in the **Tools** menu only after the AD DS role is installed.

---

## 🗂️ What is an Organizational Unit?

An OU is a container in the directory used to organize users, computers and groups. OUs matter for two reasons:

- **Organization:** Objects are grouped by department or function, so they are easy to find and manage.
- **Group Policy:** Policies are linked to OUs, so a policy applies to everyone in that OU.

| Setting | Value |
|---------|-------|
| **Tool** | Active Directory Users and Computers (ADUC) |
| **Domain** | `seemaenterprise.co.in` |
| **Department OUs** | IT, HR, Finance, Sales |
| **Computer OUs** | Computers, with sub-OUs Laptops and Desktops |

---

## 🧪 Lab Environment

| Component | Value |
|-----------|-------|
| **Platform** | Microsoft Azure, Germany West Central |
| **Domain** | `seemaenterprise.co.in` |
| **NetBIOS name** | `SEEMAENTERPRISE` |
| **Domain Controller** | `server2021` (Windows Server 2025 Datacenter) |
| **Client** | Windows 11 Pro, joined to the domain |

---

## 🔧 Create the OU Structure

Target structure:

```text
seemaenterprise.co.in
├── IT
├── HR
├── Finance
├── Sales
├── Computers
│   ├── Laptops
│   └── Desktops
└── Domain Controllers (default)
```

### Step 1 - Create the Department OUs

1. Open **Server Manager → Tools → Active Directory Users and Computers**.
2. Right-click the domain name `seemaenterprise.co.in` and select:

```text
New → Organizational Unit
```

3. Enter the name `IT` and click **OK**.
4. Repeat for `HR`, `Finance` and `Sales`.

> Leave **Protect container from accidental deletion** ticked. It stops an OU from being deleted by mistake.

**Screenshot: creating an OU:**

<img width="1920" height="1080" alt="New Object - Organizational Unit window with the name IT" src="https://github.com/user-attachments/assets/093e4d79-d796-4cc2-9724-46eaf95180f3" />

### Step 2 - Create the Computers OU and Its Sub-OUs

1. Right-click the domain and select **New → Organizational Unit**, and create `Computers`.
2. Right-click the new **Computers** OU, select **New → Organizational Unit**, and create `Laptops`.
3. Repeat to create `Desktops`.

### Step 3 - Check the Structure

Expand `seemaenterprise.co.in` in ADUC and check that all OUs are listed.

**Screenshot: the finished OU structure:**

<img width="1920" height="1080" alt="ADUC showing the OUs IT, HR, Finance, Sales and Computers with Laptops and Desktops" src="https://github.com/user-attachments/assets/f725ccac-27bc-4a7b-b229-9a2610106a03" />

> A new domain-joined computer, such as the Windows 11 client, lands in the default **Computers** container, not in your **Computers** OU. Move it into **Laptops** or **Desktops** if you want OU-based policy to apply to it. Group Policy can be linked to an OU, but not to the default **Users** and **Computers** containers.

---

## 🛠️ IT Support Tasks in ADUC

| Task | Where to click | Lab file |
|------|----------------|----------|
| Create an OU | Domain → **New → Organizational Unit** | This file |
| Create a user account | OU → **New → User** | [Create a New User Account](./create-user-account.md) |
| Reset a user's password | User → **Reset Password** | [Reset Active Directory User Password](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Active%20Directory/reset-password.md) |
| Unlock a locked account | User → **Properties → Account** | [Unlock a User Account](./unlock-user-account.md) |
| Disable or enable an account | User → **Disable / Enable Account** | [Enable and Disable Active Directory User Accounts](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Active%20Directory/enable-disable-users.md)|
| Find a user | **Action → Find** | [Find and Search Users in AD](./find-search-users.md) |
| Move a user between OUs | User → **Move** | [Move User Between OUs](./move-user-between-ous.md) |
| Create a security group and add members | OU → **New → Group** | [Create Active Directory Security Groups](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Active%20Directory/create-security-groups.md)
| Locate or move a computer account | Domain → **Find**, then **Move** | Not covered yet |

---

## 🔗 Lab Build Order

| Step | What was done | File |
|:----:|---------------|------|
| 1 | Created the Windows Server 2025 VM on Azure | [Create Windows Server VM](./create-windows-server-vm.md) |
| 2 | Opened Server Manager | [Server Manager Overview](./server-manager-overview.md) |
| 3 | Installed AD DS and promoted the server to a Domain Controller | [Promote to Domain Controller](./promote-to-domain-controller.md) |
| 4 | Joined the Windows 11 client to the domain | [Join Windows 11 Client to Domain](./join-windows-11-client.md) |
| 5 | Built the OU structure and managed users and groups in ADUC | This file and the tasks above |

---

## ✅ Lab Verification

| Check | Result |
|-------|--------|
| **Domain** | `seemaenterprise.co.in` ✅ |
| **Domain Controller** | `server2021` ✅ |
| **Windows 11 client** | Domain-joined ✅ |
| **ADUC** | Opened successfully ✅ |
| **OU structure** | IT, HR, Finance, Sales and Computers (Laptops, Desktops) created ✅ |
| **Computer account** | The client is visible in the **Computers** container ✅ |
| **User tasks** | User created, password reset, account unlocked, disabled and enabled, user found, user moved between OUs ✅ |
| **Security group** | `HR-Users` created with members ✅ |

---

## 💡 Next Step

→ [Group Policy](./group-policy.md)
