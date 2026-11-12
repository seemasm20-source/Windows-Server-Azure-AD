# 🗄️ File Server: Shared Folders, NTFS Permissions and Mapped Drives

[ Back to Overview] → [README.md](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/README.md)

---

## 📋 Summary

The Windows Server `server2021` is used as a file server for the `seemaenterprise.co.in` domain. A folder is shared over the network, access is controlled with share and NTFS permissions, and a domain user opens the share from the Windows 11 client by UNC path and by a mapped network drive.

---

## 💡 What is a File Server?

A file server stores files in a central place and lets users open them over the network, based on the permissions they have. Users sign in with their domain accounts, and the server checks their access every time they open a share.

| Setting | Value |
|---------|-------|
| **Server** | `server2021` (private IP `172.16.0.4`) |
| **Domain** | `seemaenterprise.co.in` |
| **Shared folder** | `C:\Companyshare` |
| **Share name** | `Companyshare` |
| **Subfolder** | `C:\Companyshare\Finance` |
| **Network path** | `\\server2021\Companyshare` |
| **Client** | Windows 11 Pro, joined to the domain |
| **Test user** | `sam@seemaenterprise.co.in` |

---

## 🔐 Share Permissions and NTFS Permissions

Access to a shared folder is controlled in two places. When a user connects over the network, **both** apply, and the **more restrictive** one wins.

| | Share permissions | NTFS permissions |
|---|---|---|
| **Where to set** | Folder **Properties → Sharing → Advanced Sharing → Permissions** | Folder **Properties → Security** tab |
| **Applies to** | Network access only | Network and local access |
| **Levels** | Read, Change, Full Control | Read, Read & execute, Modify, Full Control and more |

### NTFS Permission Levels

| Permission | Description |
|------------|-------------|
| **Full Control** | Read, modify and delete files, change permissions and take ownership |
| **Modify** | Read, write, modify and delete files. Cannot change permissions |
| **Read & Execute** | View and open files and run programs |
| **Read** | View and open files |
| **Write** | Create files and write data |

> Give access to a **security group**, such as `HR-Users`, and not to individual users. You then manage access by adding or removing group members.

---

## 🗂️ Folder Structure

```text
C:\Companyshare          ← shared as \\server2021\Companyshare
└── Finance              ← subfolder with its own NTFS permissions
    └── IT doc.txt       ← test file
```

---

## 🛠️ What Was Done in This Lab

| Task | Result | Lab file |
|------|--------|----------|
| Create and share a folder, and set share and NTFS permissions | `Companyshare` shared, and Sam allowed Change and Read | [Create Shared Folders and NTFS Permissions](./create-shared-folders.md) |
| Test NTFS permissions on a subfolder | Read & Execute allowed viewing only. Modify allowed editing, creating and deleting | [NTFS File Sharing and Permissions](./ntfs-permissions.md) |
| Map the share to a drive letter on the client | `Z:` mapped to `\\server2021\Companyshare` | [Map Network Drives Manually](./map-network-drives.md) |

---

## 🔧 How the Client Reaches the Share

| Method | How | Example |
|--------|-----|---------|
|Universal Naming Convention ( **UNC path by name**) | **Windows key + R**, then enter the path | `\\server2021\Companyshare` |
| **UNC path by IP** | Same, using the server's private IP | `\\172.16.0.4\Companyshare` |
| **Mapped drive** | File Explorer → **This PC** → **Map network drive** | `Z:` |

---





## ✅ Lab Verification

| Check | Result |
|-------|--------|
| **Folder shared** | `\\server2021\Companyshare` is available ✅ |
| **Share permission** | Sam has Change and Read ✅ |
| **Read & Execute** | Sam can open and read files, but cannot save changes to the server ✅ |
| **Modify** | Sam can edit, save, create and delete files ✅ |
| **Access by name and IP** | The share opens by `\\server2021\...` and `\\172.16.0.4\...` ✅ |
| **Mapped drive** | `Z:` is listed under **This PC** and opens the share ✅ |

---

## 💡 Next Step

→ [Group Policy (GPO) – GitHub Projects](https://github.com/seemasm20-source/Windows-Server-Azure-AD/tree/main/Group%20Policy%20(GPO))
