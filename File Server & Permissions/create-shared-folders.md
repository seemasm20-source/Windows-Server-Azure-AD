# 🖥️ Create Shared Folders and NTFS Permissions

[ Back to Overview] → [File Server Overview – Windows Server](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/File%20Server%20%26%20Permissions/fileserver-overview.md)

---

## 📋 Summary

Create a shared folder on the Windows Server, give a domain user access with share permissions and NTFS permissions, and open the share from the Windows 11 client.

---

## 💡 Share Permissions and NTFS Permissions

Access to a shared folder is controlled in two places. When a user connects over the network, **both** apply, and the **more restrictive** one wins.

| | Share permissions | NTFS permissions |
|---|---|---|
| **Where to set** | Folder **Properties → Sharing → Advanced Sharing → Permissions** | Folder **Properties → Security** tab |
| **Applies to** | Only network access to the share | Network access and local access |
| **Levels** | Read, Change, Full Control | Read, Read & execute, Modify, Full Control and more |

| Setting | Value |
|---------|-------|
| **Folder** | `C:\Companyshare` |
| **Share name** | `Companyshare` |
| **Server** | `server2021` (private IP `172.16.0.4`) |
| **User tested** | `sam@seemaenterprise.co.in` |

> Best practice is to give access to a **security group** such as `HR-Users`, not to individual users. You then manage access by adding or removing group members.

---

## 🔧 Part 1 - Create and Share the Folder (Windows Server)

1. On the Windows Server, open **File Explorer** and go to the **C:** drive.
2. Right-click an empty space and select **New → Folder**. Name it `Companyshare`.
3. Open the folder and create an empty test file inside it, for example `test.txt`.
4. Right-click the `Companyshare` folder and select **Properties → Sharing** tab → **Advanced Sharing**.
5. Tick **Share this folder**.
6. Click **Permissions**.
7. Select **Everyone** and click **Remove**.
8. Click **Add...**, type the user or group (for example `Domain Users`, a group such as `HR-Users`, or the user `sam@seemaenterprise.co.in`), and click **Check Names**, then **OK**.
9. Tick **Allow** for **Change** (this also selects **Read**).
10. Click **Apply**, then **OK**.

**Screenshots: sharing the folder:**

<img width="1920" height="1080" alt="Creating the Companyshare folder on the C: drive" src="https://github.com/user-attachments/assets/9fdcd173-ab07-4877-a128-096e7e94cb4e" />

<img width="1920" height="1080" alt="Folder Properties Sharing tab with Advanced Sharing" src="https://github.com/user-attachments/assets/ed2e56f9-c6d2-427d-95c6-bbd40da7f0ca" />

<img width="1920" height="1080" alt="Advanced Sharing with Share this folder ticked" src="https://github.com/user-attachments/assets/f775a774-0426-4107-82de-122fb1d5eb67" />

<img width="1920" height="1080" alt="Share permissions with Everyone removed and the domain user added" src="https://github.com/user-attachments/assets/7e2427f0-7a1c-42cc-bdd2-0d6c98a8818d" />

<img width="1920" height="1080" alt="Share permissions showing Change and Read allowed" src="https://github.com/user-attachments/assets/2030d9b7-a70b-4b7f-bb02-6908eb0fca21" />

---

## 🔧 Part 2 - Set NTFS Permissions (Windows Server)

1. Right-click the `Companyshare` folder and select **Properties → Security** tab.
2. Click **Edit...**, then **Add...**.
3. Type the same user or group, click **Check Names**, then **OK**.
4. Tick **Allow** for **Modify** (or **Read & execute** for read-only access).
5. Click **Apply**, then **OK**.

> The share permission and the NTFS permission must both allow the action. If the share allows **Change** but NTFS allows only **Read**, the user can only read.

---

## 🔧 Part 3 - Access the Share from the Windows 11 Client

1. Sign in to the Windows 11 client VM as `sam@seemaenterprise.co.in`.
2. Press **Windows key + R** to open the **Run** dialog.
3. Enter the path to the share in UNC format, using the server name or its private IP:

```text
\\SERVER2021\Companyshare
\\172.16.0.4\Companyshare
```

4. Press **Enter**. The shared folder opens, and the test file is visible.

**Screenshots: opening the share on the client:**

<img width="2160" height="2753" alt="Run dialog on the Windows 11 client with the UNC path to the share" src="https://github.com/user-attachments/assets/b8f1daa4-9f3f-4d75-828f-6ffb6419696e" />

<img width="2160" height="2880" alt="The Companyshare folder opened on the Windows 11 client" src="https://github.com/user-attachments/assets/d85290a7-1814-4f34-a81b-0185529bff2c" />

> If you get "network path not found", check the SMB inbound firewall rule, as in the Firewall Connectivity Issues scenario.

---

## ✅ Verification

| Check | Where | Expected Result |
|-------|-------|-----------------|
| Folder shared | Server → Properties → Sharing | Network path `\\SERVER2021\Companyshare` is shown ✅ |
| Share permission | Advanced Sharing → Permissions | Selected user or group has Change and Read ✅ |
| NTFS permission | Properties → Security | Selected user or group has Modify ✅ |
| Access by name | Client → Run → `\\SERVER2021\Companyshare` | Folder opens ✅ |
| Access by IP | Client → Run → `\\172.16.0.4\Companyshare` | Folder opens ✅ |

---

## 💡 Next Step

→ [NTFS Permissions](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/File%20Server%20%26%20Permissions/ntfs-permissions.md)


























































































