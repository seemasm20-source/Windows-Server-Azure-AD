# 🪟 Windows Server on Azure: Active Directory Portfolio

**Portfolio:** IT Help Desk Tier 1 & Tier 2 - Windows Server Labs

**Platform:** Microsoft Azure (Germany West Central)

**Purpose:** Demonstrate hands-on Windows Server and Active Directory administration for IT Help Desk Tier 1 and Tier 2 roles

**Author:** Seema Soapanahalli Mallikarjunaiah

---

## 📌 About This Portfolio

This portfolio documents home labs built on Microsoft Azure with Windows Server 2025 and Windows 11 Pro. It covers IT Help Desk Tier 1 and Tier 2 tasks: Active Directory administration, file server management, Group Policy, Event Viewer analysis and remote support tools.

Each lab follows the same flow: summary, steps, verification and screenshots.

> **Lab Note:** Labs were built on Azure virtual machines. Where a fault could not be reproduced, such as an application crash, the file uses an illustrative example and says so.

---

## 🧪 Lab Environment

| Component | Detail |
|-----------|--------|
| **Server OS** | Windows Server 2025 Datacenter |
| **Client OS** | Windows 11 Pro |
| **Platform** | Microsoft Azure, Germany West Central |
| **Domain** | `seemaenterprise.co.in` |
| **NetBIOS name** | `SEEMAENTERPRISE` |
| **Domain Controller** | `server2021` (private IP `172.16.0.4`) |
| **Client** | Windows 11 Pro, joined to the domain |
| **Test user** | `Sam` |

---

## 📁 Portfolio Structure

| Section | Topic | Key Skills |
|---------|-------|------------|
| **Section 1** | Azure and Domain Controller Setup | Deploy the VM, Server Manager, promote to a Domain Controller, join a client to the domain |
| **Section 2** | Active Directory | Users, passwords, lockouts, groups, OUs |
| **Section 3** | File Server and Permissions | Shares, NTFS permissions, mapped drives |
| **Section 4** | Group Policy | GPOs, OU linking, USB, drives, password and lockout, Control Panel |
| **Section 5** | Remote Support Tools | RDP, Computer Management, Event Viewer, UNC paths |
| **Section 6** | Event Viewer | Account, sign-in, shutdown and application events |

---

## 🖥️ Section 1 - Azure and Domain Controller Setup

| Lab | What it covers | File |
|-----|----------------|------|
| **Create Windows Server VM** | Deploy a Windows Server 2025 VM on Azure | [Create Windows Server VM](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Windows%20Server%20Azure/Create%20Server%20VM.md) |
| **Server Manager Overview** | The main console for managing the server | [Server Manager Overview](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Windows%20Server%20Azure/Server-manager-overview.md) |
| **Promote to Domain Controller** | Install AD DS and create the forest `seemaenterprise.co.in` |[Promote to Domain Controller](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Windows%20Server%20Azure/promote-to-domaincontroller.md) |
| **Create Windows 11 Client VM** | Deploy a Windows 11 Pro VM on Azure as the client machine | [Create Client VM](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Windows%20Server%20Azure/create-clientvm-machine.md) |
| **Join Windows 11 Client to Domain** | Set DNS to the DC and join the client to the domain | [Join Client to Domain](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Windows%20Server%20Azure/join-client-to-domain.md) |

---

## 👥 Section 2 - Active Directory

| Lab | What it covers | File |
|-----|----------------|------|
| **ADUC and OU Structure** | Active Directory Users and Computers, and the department OUs | [ADUC Overview and Organizational Unit Structure](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Active%20Directory/aduc-overview-and-organisation-unit-structure.md) |
| **Create a New User Account** | Create a user in an OU and test the sign-in | [Create User Account](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Active%20Directory/create-user-account.md) |
| **Reset a User Password** | Temporary password and forced change at sign-in | [Reset Active Directory User Password](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Active%20Directory/reset-password.md) |
| **Unlock a User Account** | Unlock a locked-out account | [Unlock an Active Directory User Account](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Active%20Directory/unlock-account.md) |
| **Enable and Disable User Accounts** | Block and restore sign-in | [Enable and Disable Active Directory User Accounts](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Active%20Directory/enable-disable-users.md)) |
| **Find and Search Users** | Search the domain with Find | [Find a User Account in Active Directory](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Active%20Directory/find-user-in-ad.md) |
| **Move User Between OUs** | Change which policies apply to a user | [Move Active Directory Users Between OUs](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Active%20Directory/move-users-between-ou.md) |
| **Create Security Groups** | Create a group and add members | [Create Active Directory Security Groups](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Active%20Directory/create-security-groups.md) |

---

## 🗄️ Section 3 - File Server and Permissions

| Lab | What it covers | File |
|-----|----------------|------|
| **File Server** | Overview of shares, NTFS permissions and mapped drives | [File Server Overview](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/File%20Server%20%26%20Permissions/fileserver-overview.md) |
| **Create Shared Folders** | Share a folder, set share and NTFS permissions | [Create Shared Folders](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/File%20Server%20%26%20Permissions/create-shared-folders.md) |
| **NTFS Permissions** | Test Read & Execute and Modify from the client | [NTFS Permissions](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/File%20Server%20%26%20Permissions/ntfs-permissions.md) |
| **Map Network Drives Manually** | Map a share to a drive letter in File Explorer | [Map Network Drives](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/File%20Server%20%26%20Permissions/map-network-drives.md) |

---

## 📜 Section 4 - Group Policy

| Lab | Policy type | What it covers | File |
|-----|-------------|----------------|------|
| **Group Policy Overview and OU Linking** | Not applicable | How GPOs work, creating and linking a GPO | [Group Policy Overview](./group-policy-overview.md) |
| **Disable USB Storage** | Computer | Block USB storage devices | [Disable USB Storage](./disable-usb-storage.md) |
| **Drive Mapping with Group Policy** | User | Map `Companyshare` at sign-in | [Drive Mapping with Group Policy](./drive-mapping-gpo.md) |
| **Password and Lockout Policy** | Computer (Account Policies) | Password rules and account lockout | [Password and Lockout Policy](./password-lockout-policy.md) |
| **Restrict Control Panel Access** | User | Block or hide Control Panel items | [Restrict Control Panel Access](./restrict-control-panel.md) |
| **Troubleshoot GPO Not Applying** | Not applicable | Checklist, `gpupdate` and `gpresult` | [Troubleshoot GPO Not Applying](./troubleshoot-gpo.md) |

---

## 🔌 Section 5 - Remote Support Tools

| Lab | What it covers | File |
|-----|----------------|------|
| **Remote Support Tools Overview** | Choosing the right remote tool | [Remote Support Tools Overview](https://github.com/seemasm20-source/Windows-Server-Azure-AD/tree/main/Remote%20Support%20Tools) |
| **Remote Desktop Protocol (RDP)** | Connect with `mstsc` and troubleshoot RDP | [Remote Desktop Protocol](https://github.com/seemasm20-source/Windows-Server-Azure-AD/tree/main/Remote%20Support%20Tools) |
| **Remote Computer Management** | Manage another computer from `compmgmt.msc` | [Remote Computer Management](https://github.com/seemasm20-source/Windows-Server-Azure-AD/tree/main/Remote%20Support%20Tools) |
| **Remote Event Viewer** | Read the logs of another computer | [Remote Event Viewer](https://github.com/seemasm20-source/Windows-Server-Azure-AD/tree/main/Remote%20Support%20Tools) |
| **UNC Path Access** | Open a share with `\\server2021\Companyshare` | [UNC Path Access](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Remote%20Support%20Tools/unc-path-access.md) |

---

## 📊 Section 6 - Event Viewer

| Event ID | What it shows | Log | File |
|----------|---------------|-----|------|
| **Overview** | Logs, event fields and the labs below | | [Event Viewer Overview](./event-viewer-overview.md) |
| **4740** | A user account was locked out | Security | [Event ID 4740](./event-id-4740.md) |
| **4720** | A user account was created | Security | [Event ID 4720](./event-id-4720.md) |
| **4625 and 4624** | A failed and a successful logon | Security | [Event ID 4625 and 4624](./event-id-4625-4624.md) |
| **41** | An unexpected shutdown (Kernel-Power) | System | [Event ID 41](./event-id-41.md) |
| **1000** | An application crash (illustrative example) | Application | [Event ID 1000](./event-id-1000.md) |

---

## 📚 Skills Demonstrated

### Active Directory
- Deploy a Windows Server VM and promote it to a Domain Controller
- Join a Windows 11 client to the domain
- Create and manage user accounts and OUs
- Reset passwords, unlock, disable and enable accounts
- Create security groups, search for users and move users between OUs

### File Server and Permissions
- Share folders and configure NTFS and share permissions
- Apply the rule that the more restrictive permission wins
- Map network drives manually and with Group Policy
- Troubleshoot "Access denied" and "Network path not found" errors

### Group Policy
- Create and link GPOs to OUs
- Configure password and account lockout policies
- Deploy drive mappings and block USB storage
- Restrict Control Panel access
- Troubleshoot a GPO that does not apply with `gpupdate` and `gpresult`

### Event Viewer
- Trace an account lockout source (Event ID 4740)
- Audit account creation (Event ID 4720)
- Read failed and successful logons (Event IDs 4625 and 4624)
- Investigate unexpected shutdowns (Event ID 41)
- Read an application crash event (Event ID 1000)

### Remote Support Tools
- Connect with Remote Desktop (RDP)
- Manage a remote computer with Computer Management
- Read remote event logs
- Open and test shares by UNC path

---

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| Microsoft Azure | Virtual machine hosting |
| Windows Server 2025 | Domain Controller and file server |
| Windows 11 Pro | Domain-joined client |
| Active Directory Users and Computers | User, group and OU management |
| Group Policy Management Console | GPO creation and linking |
| Event Viewer | Log analysis |
| Computer Management | Remote administration |
| Remote Desktop Connection (`mstsc`) | Remote desktop access |
| Command Prompt | `gpupdate`, `gpresult`, `ipconfig`, `nslookup` |

---

## 🔗 Related Portfolios

| Portfolio | Link |
|-----------|------|
| **DNS Troubleshooting Portfolio** | [DNS Portfolio](https://github.com/seemasm20-source/networking-labs/tree/main/03-dns-portfolio) |
| **DHCP Configuration Portfolio** | [DHCP Portfolio](https://github.com/seemasm20-source/networking-labs/tree/main/02-dhcp-configuration) |
| **TCP/IP Network Troubleshooting Portfolio** | [TCP/IP Portfolio](https://github.com/seemasm20-source/networking-labs/tree/main/04-tcp-ip-network-troubleshooting) |

---

## 🎓 Learning Outcome

This portfolio provided hands-on experience with a small Active Directory environment on Azure, from deploying the server to managing users, policies, file shares and logs. It built practical skills for daily help desk tasks, such as resetting passwords, finding the cause of a lockout and troubleshooting a GPO that does not apply, relevant to IT Help Desk Tier 1 and Tier 2 roles.

---

## ✅ Conclusion

A Windows Server 2025 VM was deployed on Azure and promoted to a Domain Controller, a Windows 11 client was joined to the domain, and users, groups, OUs, file shares, Group Policy, Event Viewer analysis and remote support tools were configured and tested.

Planned additions: VPN configuration, Windows Remote Assistance and Quick Assist.

> **Note:** This portfolio is actively being built. Labs and screenshots are added as each section is completed.
