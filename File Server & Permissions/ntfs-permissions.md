# 🖥️ NTFS File Sharing and Permissions

[ Back to Overview] → [README.md](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/README.md)

---

## 📋 Summary

Set NTFS permissions on a subfolder of the shared folder `Companyshare`, and test them from the Windows 11 client. The test gives the user **Read & Execute** first, which allows viewing only, then **Modify**, which allows editing.

---

## 💡 What are NTFS Permissions?

NTFS (New Technology File System) is the standard file system of modern Windows. NTFS permissions control which users and groups can access files and folders, and what they can do with them. They apply to both local and network access.

When a folder is shared over the network, users open it with a UNC path, for example `\\server2021\Companyshare`. Access is controlled by the **share permissions** and the **NTFS permissions** together. The more restrictive one wins.

| Permission | Description |
|------------|-------------|
| **Full Control** | Read, modify and delete files, change permissions and take ownership |
| **Modify** | Read, write, modify and delete files. Cannot change permissions |
| **Read & Execute** | View and open files and run programs. Includes Read and List folder contents |
| **Read** | View and open files |
| **Write** | Create files and write data |

| Setting | Value |
|---------|-------|
| **Shared folder** | `C:\Companyshare` (share permissions: Change and Read for `Sam`) |
| **Subfolder** | `C:\Companyshare\Finance` |
| **Test file** | `IT doc.txt` |
| **User tested** | `sam@seemaenterprise.co.in` |
| **Server** | `server2021` (private IP `172.16.0.4`) |

---

## 🔧 Part 1 - Create the Subfolder (Windows Server)

1. On the Windows Server, open **File Explorer** and go to `C:\Companyshare`.
2. Right-click an empty space and select **New → Folder**. Name it `Finance`.
3. Open the `Finance` folder and create a text file named `IT doc`.

**Screenshot: Finance folder and test file:**

<img width="1920" height="1080" alt="The Finance folder with the IT doc file inside C:\Companyshare" src="https://github.com/user-attachments/assets/09b58706-83ff-4a42-9811-2f04aa788295" />

---

## 🔧 Part 2 - Set Read & Execute for Sam (Windows Server)

1. Right-click the `Finance` folder and select **Properties**.
2. Open the **Security** tab and click **Edit...**
3. Click **Add...**, type `Sam`, click **Check Names**, then **OK**.
4. With `Sam` selected in the top box, tick **Allow** for **Read & execute** in the bottom box. This also ticks **List folder contents** and **Read**.
5. Click **Apply**, then **OK**.

**Screenshots: setting Read & Execute:**

<img width="1920" height="1080" alt="Finance folder Properties Security tab" src="https://github.com/user-attachments/assets/2f1096c8-be72-4097-b76f-d2301e0bbc79" />

<img width="1920" height="1080" alt="Permissions window with Sam added" src="https://github.com/user-attachments/assets/02ce844e-ab6a-47c7-ac41-ff7192e7948c" />

<img width="1920" height="1080" alt="Sam with Read and Execute permission allowed" src="https://github.com/user-attachments/assets/ef86d4a3-ba64-4a51-bd23-d0ffcdbf566f" />

---

## 🔧 Part 3 - Test Read & Execute (Windows 11 Client)

1. Sign in to the Windows 11 client as `sam@seemaenterprise.co.in`.
2. Press **Windows key + R** and open the folder:

```text
\\172.16.0.4\Companyshare\Finance
```

3. Open the `IT doc` file. The file opens and can be read.
4. Make a change and try to save it. Windows does not allow saving to the original file on the server. It opens a **Save As** window and asks for another location, such as the Desktop or Documents.
5. Windows shows a **Destination Folder Access Denied** message when saving into the server folder, because Sam's NTFS permission is read-only.

**Screenshots: Read & Execute test on the client:**

<img width="2160" height="2840" alt="IT doc opened on the client in read-only mode" src="https://github.com/user-attachments/assets/8294ec07-55a8-4fdd-86a3-434f2eddafb6" />

<img width="2072" height="3050" alt="Destination Folder Access Denied message when saving to the server folder" src="https://github.com/user-attachments/assets/c85ff27b-8beb-496d-8771-1674134d4615" />

---

## 🔧 Part 4 - Change Sam's Permission to Modify (Windows Server)

1. Right-click the `Finance` folder, select **Properties → Security**, and click **Edit...**
2. Select `Sam` in the top box. Do not add Sam again.
3. Tick **Allow** for **Modify**. This also ticks **Read & execute**, **List folder contents**, **Read** and **Write**.
4. Click **Apply**, then **OK**.

**Screenshots: setting Modify:**

<img width="1920" height="1080" alt="Sam with Modify permission allowed" src="https://github.com/user-attachments/assets/e0540fe8-5344-4c78-8752-62bc8ddfbf07" />

<img width="1920" height="1080" alt="Finance folder Properties after applying Modify" src="https://github.com/user-attachments/assets/daef3de9-d1ea-4387-9517-b48200b23669" />

---

## 🔧 Part 5 - Test Modify (Windows 11 Client)

1. Sign out of the client and sign in again as Sam, so the new permission applies to the session.
2. Open `\\172.16.0.4\Companyshare\Finance` again.
3. Open `IT doc`, edit it and click **Save**. The file saves in place on the server.
4. Create a new file in the folder, and delete a test file. Both work.

The next person who opens the file sees the saved changes, because the file is updated on the server.

**Screenshot: Modify test on the client:**

<img width="2160" height="2095" alt="IT doc edited and saved on the server by Sam with Modify permission" src="https://github.com/user-attachments/assets/e984b01d-3ada-448d-b629-82a83a5be65a" />

---

## ✅ Verification

| Permission | Open and read | Edit and save | Create files | Delete files |
|------------|:-------------:|:-------------:|:------------:|:------------:|
| **Read & Execute** | ✅ | ❌ Save As only | ❌ | ❌ |
| **Modify** | ✅ | ✅ | ✅ | ✅ |

---

## 💡 Next Step

→ [Group Policy](./group-policy.md)


























































































## 🖥️NTFS File Sharing & Permissions:
 
NTFS stands for New Technology File System. It is the standard file system used by modern Windows operating systems to store and manage files and folders.

NTFS permissions control which users and groups can access files and folders and what actions they can perform, such as Read, Write, Modify, or Full Control.

When a folder is shared over a network, users can access it using a UNC path such as: \\server2021\CompanyData


## Key NTFS Permissions: 

| Permission     | Description                                  |
| -------------- | -------------------------------------------- |
| Full Control   | Read, modify, delete, and change permissions |
| Modify         | Read, write, modify, and delete              |
| Read & Execute | View files and execute programs              |
| Read           | View and open files                          |
| Write          | Create or modify files                       |







## Create NTFS File Sharing Permissions:

 ## Steps to do in Windows Server machine:-


 1. Create the Subfolder.
 2. On your Windows Server, open File Explorer and navigate into C:\CompanyShare.
 3. Right-click an empty space, choose New > Folder, and name it Finance . Inside Finance create a file/doc by name IT doc
 4. Open the Security Settings
 5. Right-click your new Finance folder and select Properties.
 6. Switch to the Security tab at the top.
 7. Set Specific NTFS Permissions for the User "__SAM__" for __READ & EXECUTE PERMISSION__







## Now back on the main Security tab screen:-

 1. Click the Edit... button.
 2. Click Add..., type __SAM__, and click Check Names. Then click OK.
 3. With __SAM__ highlighted in the top box, go to the bottom box and check the box for __READ & EXECUTE__. 
      (This automatically checks Read and List folder contents, allowing the users to view  files).
 4. Click Add... again, type __SAM__ and click Check Names. Then click OK.
 5. Check whether access is given for __READ & EXECUTE__ in client machine

   ## Set Specific NTFS Permissions for the User "__SAM__" for __MODIFY PERMISSION__

 1. Click the Edit... button.
 2. Click Add..., type __SAM__, and click Check Names. Then click OK.
 3. With __SAM__ highlighted in the top box, go to the bottom box and check the box for __MODIFY__. (This automatically checks Read, Write and List folder contents, allowing the       users to create and edit files).
 4. Click Add... again, type __SAM__ and click Check Names. Then click OK.
 5. Check whether access is given for __MODIFY__
 6. Click Apply and OK to close all properties windows.




## Steps to do in Windows Client machine :-



 1. Log into the Windows 11 Client as sam. Open the share via \\172.16.0.4\CompanyShare\Finance. Try to right-click and get in to IT doc text file .

 2. Firstly checking Read & Execute (Viewer mode): You can open and read the document IT.doc cleanly. If you make edits and click Save, Windows blocks you from modifying the           original file on the server. Instead, it forces a "Save As" window to pop up, requiring you to choose an alternate destination like your Desktop or your personal Documents         folder to keep your changes.

 3. Windows 11 will show a popup saying    "Destination Folder Access Denied" because his NTFS permission is Read Only.

 4. Log out and sign back in as sam again. Go to the same folder. You have access to Modify (Editor Mode): You can read, write, edit, and safely click Save directly inside the         document. The file updates instantly in place on the server and the next coworker who opens that exact file will immediately see your new edits.He will be able to create,          write, edit and delete files perfectly because his NTFS permission is set to Modify.





















<img width="1920" height="1080" alt="Screenshot (615)" src="https://github.com/user-attachments/assets/09b58706-83ff-4a42-9811-2f04aa788295" />





































<img width="1920" height="1080" alt="Screenshot (616)" src="https://github.com/user-attachments/assets/2f1096c8-be72-4097-b76f-d2301e0bbc79" />














































<img width="1920" height="1080" alt="Screenshot (617)" src="https://github.com/user-attachments/assets/02ce844e-ab6a-47c7-ac41-ff7192e7948c" />















<img width="1920" height="1080" alt="Screenshot (618)" src="https://github.com/user-attachments/assets/ef86d4a3-ba64-4a51-bd23-d0ffcdbf566f" />















































<img width="1920" height="1080" alt="Screenshot (620)" src="https://github.com/user-attachments/assets/e0540fe8-5344-4c78-8752-62bc8ddfbf07" />

































<img width="1920" height="1080" alt="Screenshot (621)" src="https://github.com/user-attachments/assets/daef3de9-d1ea-4387-9517-b48200b23669" />






































<img width="2160" height="2840" alt="79C118FC-B953-4E27-9C05-DEEBA445530A" src="https://github.com/user-attachments/assets/8294ec07-55a8-4fdd-86a3-434f2eddafb6" />




































<img width="2072" height="3050" alt="9F3C1DC8-0F83-4D46-8FC3-A991615A793F" src="https://github.com/user-attachments/assets/c85ff27b-8beb-496d-8771-1674134d4615" />

















































<img width="2160" height="2095" alt="EE5A15E3-1E2F-4992-ACEA-36791A790E23" src="https://github.com/user-attachments/assets/e984b01d-3ada-448d-b629-82a83a5be65a" />
