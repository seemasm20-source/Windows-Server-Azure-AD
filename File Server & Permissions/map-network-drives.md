
# 🖥️ Map Network Drives Manually

[ Back to Overview] → [README.md](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/README.md)

---

## 📋 Summary

Map a shared folder on the Windows Server to a drive letter on the Windows 11 client, using File Explorer. The user then opens the share like a local drive, without typing the network path each time.

---

## 💡 What is a Mapped Network Drive?

A mapped network drive is a drive letter, such as `Z:`, that points to a shared folder on another computer. It appears under **This PC** in File Explorer, so users can open the share in one click.

| Setting | Value |
|---------|-------|
| **Server** | `server2021` |
| **Shared folder** | `Companyshare` |
| **Network path** | `\\server2021\Companyshare` |
| **User** | `sam@seemaenterprise.co.in` (Read and Change share permissions) |
| **Drive letter** | `Z:` |

> The share and its permissions are created in the [Create Shared Folders and NTFS Permissions](./create-shared-folders.md) file. If `Companyshare` already exists, skip Part 1 and just copy the network path.

---

## 🔧 Part 1 - Prepare the Shared Folder (Windows Server)

1. Open **File Explorer** and go to the location for the folder, for example `C:\`.
2. Right-click an empty space and select **New → Folder**. Name it `Companyshare`.
3. Right-click the folder and select **Properties → Sharing** tab → **Advanced Sharing**.
4. Tick **Share this folder**.
5. Click **Permissions**, add the user `Sam`, and allow **Change** (this also selects **Read**).
6. Click **OK**, then **Apply**.
7. On the **Sharing** tab, copy the **Network Path**. It looks like this:

```text
\\server2021\Companyshare
```

**Screenshots: sharing the folder on the server:**

<img width="1920" height="1080" alt="Folder Properties Sharing tab showing the network path" src="https://github.com/user-attachments/assets/d3a1555f-5293-4c54-9eb8-f755c33ff851" />

<img width="1920" height="1080" alt="Advanced Sharing with Share this folder ticked" src="https://github.com/user-attachments/assets/9e4f2813-220e-45a1-85d6-3abd5aa5dcef" />

<img width="1920" height="1080" alt="Share permissions with the user Sam allowed Change and Read" src="https://github.com/user-attachments/assets/b69fde9d-f79e-4988-a665-480787ea92b1" />

---

## 🔧 Part 2 - Map the Drive on the Client (File Explorer)

1. On the Windows 11 client, sign in as `sam@seemaenterprise.co.in`.
2. Open **File Explorer** (**Windows key + E**) and select **This PC** in the left pane.
3. Click the **three dots (...)** in the top toolbar and select **Map network drive**.
4. In the **Map Network Drive** window, set:

| Field | Value |
|-------|-------|
| **Drive** | `Z:` (any free drive letter) |
| **Folder** | `\\server2021\Companyshare` |
| **Reconnect at sign-in** | Ticked, so the drive stays after a restart |
| **Connect using different credentials** | Tick only if the client sign-in differs from the account that has access to the share |

5. Click **Finish**.

**Screenshots: mapping the drive on the client:**

<img width="2160" height="2371" alt="This PC toolbar menu with Map network drive selected" src="https://github.com/user-attachments/assets/cbf5e807-9220-4855-99dd-6d19495506d7" />

<img width="2160" height="2766" alt="Map Network Drive window with drive Z and the folder path entered" src="https://github.com/user-attachments/assets/025ea7bf-11bc-42d3-8957-874ab686f6eb" />

<img width="2160" height="2766" alt="The mapped drive Companyshare shown under This PC" src="https://github.com/user-attachments/assets/ca8a56d4-bf5f-4811-80d7-fe87b7c42d8a" />

---

## ✅ Verification

| Check | Where | Expected Result |
|-------|-------|-----------------|
| Drive appears | File Explorer → This PC | `Companyshare (\\server2021) (Z:)` is listed under **Network locations** ✅ |
| Share opens | Double-click the drive | The contents of `Companyshare` are shown ✅ |
| Drive persists | After a restart and sign-in | The drive is still mapped ✅ |

---

## 💡 Next Step

→ [Map Network Drives with Group Policy](./map-drives-group-policy.md)






















































	 

	



















































































































































































































