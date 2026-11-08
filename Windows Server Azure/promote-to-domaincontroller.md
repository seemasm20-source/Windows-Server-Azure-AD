# 🖥️ Promote to Domain Controller

[ Back to Overview] → [README.md](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/README.md)

---

## 📋 Summary

Install the Active Directory Domain Services (AD DS) role on the Windows Server VM and promote it to a Domain Controller by creating a new forest. This server will manage users, computers and policies for the lab domain.

---

## 💡 What is a Domain Controller?

A Domain Controller (DC) is a server that runs Active Directory. It stores the directory of users, computers and groups, and it authenticates sign-ins for the whole domain.

| Setting | Value |
|---------|-------|
| **Root domain name** | `seemaenterprise.co.in` |
| **NetBIOS name** | `SEEMAENTERPRISE` |
| **Forest and domain functional level** | Default for Windows Server 2025 |
| **DNS server** | Installed on the DC (default option) |

---

## 🔧 Part 1 - Install the AD DS Role

1. Open **Server Manager → Manage → Add Roles and Features**.
2. Choose **Role-based or feature-based installation** and select the local server.
3. Select the role **Active Directory Domain Services**, accept the required features and select **Install**.

**Screenshots: Add Roles and Features and AD DS installation:**

<img width="1920" height="1080" alt="Add Roles and Features wizard with Active Directory Domain Services selected" src="https://github.com/user-attachments/assets/79feb6fd-6290-4373-b53a-3327704cf094" />

<img width="1920" height="1080" alt="AD DS role installation progress" src="https://github.com/user-attachments/assets/0658581a-7bad-4df4-a8dd-ecef749a7f1d" />

---

## 🔧 Part 2 - Promote the Server to a Domain Controller

1. When the installation finishes, select the **notification flag** in Server Manager, then **Promote this server to a domain controller**.
2. Choose **Add a new forest** and enter the root domain name: `seemaenterprise.co.in`.
3. Keep **DNS server** and **Global Catalog** selected, and set the **Directory Services Restore Mode (DSRM)** password.
4. Confirm the NetBIOS name: `SEEMAENTERPRISE`.
5. Review the options, wait for the prerequisites check, then select **Install**.
6. The server restarts automatically, and the RDP session disconnects.

> **DSRM password:** Store it in a password manager. It is used to repair Active Directory in recovery mode, and it should be different from the administrator password. Never show it in screenshots or in the repository.

> **DNS delegation warning:** A message such as "A delegation for this DNS server cannot be created" is normal in a new lab forest. It is not a failure.

**Screenshots: promotion wizard:**

<img width="1920" height="1080" alt="Post-deployment configuration: Promote this server to a domain controller" src="https://github.com/user-attachments/assets/a7e06df1-782c-47db-9ff5-802a60676185" />

<img width="1920" height="1080" alt="Deployment Configuration with Add a new forest and root domain name" src="https://github.com/user-attachments/assets/cef6267e-d6ef-4710-ab57-04e87714eb9d" />

<img width="1920" height="1080" alt="Domain Controller Options and DSRM password settings" src="https://github.com/user-attachments/assets/d6c0e5c1-ed20-40f2-9a61-281175c57bab" />

<img width="1920" height="1080" alt="Additional Options showing the NetBIOS domain name" src="https://github.com/user-attachments/assets/a9f5035d-a5f0-4305-8d33-527ae3a0164a" />

---

## 🔧 Part 3 - Sign In and Verify

1. Wait a few minutes, then reconnect to the VM with Remote Desktop.
2. Sign in with the domain account: `SEEMAENTERPRISE\<your-admin-username>`.
3. In Server Manager, open **Tools** and check that **Active Directory Users and Computers** is listed.
4. Go to **Local Server** and check the domain name.

**Screenshots: sign-in and domain check:**

<img width="1920" height="1080" alt="Server Manager Tools menu showing Active Directory Users and Computers" src="https://github.com/user-attachments/assets/2b21f7ab-753e-4ee6-8a8a-85f8e32a6b1a" />

<img width="1920" height="1080" alt="Server Manager Local Server showing the domain seemaenterprise.co.in" src="https://github.com/user-attachments/assets/f792c799-23c6-4ac5-80fa-7565b9177d81" />

---

## ✅ Verification

| Check | Where | Expected Result |
|-------|-------|-----------------|
| AD DS role installed | Server Manager → Dashboard | AD DS and DNS appear in the roles list ✅ |
| Domain name | Local Server | `seemaenterprise.co.in` ✅ |
| Sign-in | Remote Desktop | `SEEMAENTERPRISE\<your-admin-username>` works ✅ |
| Admin tool | Tools menu | Active Directory Users and Computers is available ✅ |

---


## 💡 Next Step

→ [Create Windows 11 Pro Client VM](./create-windows-11-vm.md)































































































