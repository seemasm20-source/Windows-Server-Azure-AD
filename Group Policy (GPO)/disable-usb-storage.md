# 🖥️ Disable USB Storage with Group Policy

[ Back to Overview] → [README.md](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/README.md)

---

## 📋 Summary

Create a Group Policy Object (GPO) that blocks USB storage devices on domain computers, link it to an Organizational Unit (OU), and test it on the Windows 11 client. This helps prevent data from being copied to removable drives.

---

## 💡 What is Group Policy?

Group Policy lets an administrator apply settings to many users and computers at once from the Domain Controller. A policy is stored in a **GPO** and **linked** to a domain or an OU. Every computer or user in that OU then receives the settings.

| Setting | Value |
|---------|-------|
| **Tool** | Group Policy Management (`gpmc.msc`) on the Domain Controller |
| **GPO name** | `GPO_Disable_USB_Storage` |
| **Policy type** | Computer Configuration |
| **Policy path** | Computer Configuration → Policies → Administrative Templates → System → Removable Storage Access |
| **Linked to** | `IT` OU |

| Policy option | Effect |
|---------------|--------|
| **All Removable Storage classes: Deny all access** | Blocks all access to removable storage. This is the fastest, catch-all setting |
| **Removable Disks: Deny write access** | The user can open files on the USB drive but cannot copy files to it (read-only USB) |

> **All Removable Storage classes: Deny all access** also affects other removable devices, such as CDs, DVDs and phones connected as portable devices, and it applies to administrators too.

---

## 🔧 Steps

### Step 1 - Create a Dedicated GPO

1. On the Domain Controller, open **Group Policy Management** (`gpmc.msc`).
2. In the left pane, expand the domain, right-click **Group Policy Objects** and select **New**.
3. Name it `GPO_Disable_USB_Storage` and click **OK**.
4. Right-click the new GPO and select **Edit**.

**Screenshots: creating the GPO:**

<img width="1920" height="1080" alt="Group Policy Management with the new GPO window" src="https://github.com/user-attachments/assets/71bb19a3-de43-42d1-9f8a-b8af013c2660" />



### Step 2 - Configure the USB Restrictions

In the Group Policy Management Editor, go to:

```text
Computer Configuration → Policies → Administrative Templates → System → Removable Storage Access
```

Choose the setting that fits the goal:

| Goal | Setting to enable |
|------|-------------------|
| **Block USB storage completely** | Double-click **All Removable Storage classes: Deny all access**, select **Enabled** and click **OK** |
| **Allow reading but block copying files to the USB drive** | Leave "Deny all access" **Not configured**. Double-click **Removable Disks: Deny write access**, select **Enabled** and click **OK** |

**Screenshots: configuring the policy:**


<img width="1920" height="1080" alt="GPO_Disable_USB_Storage created and opened for editing" src="https://github.com/user-attachments/assets/3db6f84d-3c8d-4502-92f8-8dff856764a6" />



<img width="1920" height="1080" alt="GPO_Disable_USB_Storage linked to the IT OU in Group Policy Management" src="https://github.com/user-attachments/assets/c4255ccc-5190-4b6c-a570-b3be29b763f9" />


### Step 3 - Link the GPO to the OU

1. Close the editor window.
2. In Group Policy Management, find the OU that contains the **computer accounts** to restrict. In this lab it is the `IT` OU.
3. Right-click the OU and select **Link an Existing GPO...**
4. Select `GPO_Disable_USB_Storage` and click **OK**.

> Because this is a **Computer Configuration** policy, it applies to the **computer accounts** in the OU, not to user accounts. A new domain-joined computer lands in the default **Computers** container, and policies cannot be linked to that container. Move the client's computer account into the linked OU first.

**Screenshot: GPO linked to the OU:**

<img width="1920" height="1080" alt="Removable Storage Access policy list in the Group Policy Management Editor" src="https://github.com/user-attachments/assets/92f46bd9-491c-4b13-b80d-373455dd6e72" />

<img width="1920" height="1080" alt="The USB policy setting set to Enabled" src="https://github.com/user-attachments/assets/47f6d880-adfc-4cff-80f3-73c1191a6c04" />

### Step 4 - Test on the Client

1. On the Windows 11 client (its computer account is in the linked OU), open **Command Prompt as administrator** and run:

```text
C:\> gpupdate /force
```

2. Restart the computer if Windows asks, or to be sure the policy applies.
3. Plug in a USB flash drive and test it:

| Policy used | Expected result |
|-------------|-----------------|
| **Deny all access** | The drive cannot be used. It does not open, and files cannot be read or copied |
| **Deny write access** | Files on the drive open normally, but copying a file to the drive fails with an access denied message |


---

## ✅ Verification

| Check | Where | Expected Result |
|-------|-------|-----------------|
| GPO exists | Group Policy Management → Group Policy Objects | `GPO_Disable_USB_Storage` is listed ✅ |
| Policy enabled | GPO editor | The chosen setting is **Enabled** ✅ |
| GPO linked | Group Policy Management → `IT` OU | The GPO is listed under the OU ✅ |
| Policy applied | Client → `gpresult /r /scope computer` | `GPO_Disable_USB_Storage` is listed under **Applied Group Policy Objects** ✅ |
| USB blocked | Client | The USB drive is blocked as described in Step 4 ✅ |

---

## 💡 Next Step

→ [Map Network Drives with Group Policy](./map-drives-group-policy.md)


















































































































## 🖥️Disable USB Storage


## Step 1: Create a Dedicated GPO

1. On your Domain Controller, open Group Policy Management (gpmc.msc).
   
2. Go to the Group Policy Objects folder in the left sidebar, right-click it and select New.
 
3. Name it __GPO_Disable_USB_Storage__ and click OK.

4. Right-click your new GPO and select Edit.


## Step 2: Configure the USB Removable Disk Restrictions

   Inside the editor window, navigate down through the Computer Configuration branch:

  1. Follow this path:
	  • Computer Configuration > Policies > Administrative Templates > System > Removable Storage Access

 2. In the right pane, look down the alphabetical list to find Removable Disks: Deny execute access, Removable Disks: Deny read access, and Removable Disks: Deny write access.
   
3. Configure the following based on your security goals:
   
	• To block USB storage completely (Read & Write): Double-click All Removable Storage classes: Deny all access, change it to Enabled, and click OK. (This is the fastest, catch-       all setting).

	• To allow reading files but block copying data OUT (Read-Only USB): Leave the "Deny all" setting alone. Instead, double-click Removable Disks: Deny write access, set it to          Enabled, and click OK.







## Step 3: Link the GPO to Your Target OUs

1. Close the GPO Editor window.
 
2. In the main Group Policy Management Console, locate the OU containing the computer accounts you want to restrict .

3. Right-click the IT OU and select Link an Existing GPO..

4. Select GPO_Disable_USB_Storage and click OK




## Step 4: Test it on a Client Machine
 

1. Go to a client computer that sits within that linked OU.

2. Open Command Prompt as Administrator and force the update: cmd __gpupdate /force__  

3. Restart the computer.
   
4. The Test: Plug in a standard USB flash drive.
   
	• __If you chose Deny All, the drive won't even mount or show up in This PC__.

	• __If you chose Deny Write, you will be able to open files on the flash drive, but if you try to drag a file from your desktop into the USB, Windows will block you with a         "Destination Folder Access Denied" error__.




































<img width="1920" height="1080" alt="Screenshot (647)" src="https://github.com/user-attachments/assets/71bb19a3-de43-42d1-9f8a-b8af013c2660" />





























<img width="1920" height="1080" alt="Screenshot (648)" src="https://github.com/user-attachments/assets/3db6f84d-3c8d-4502-92f8-8dff856764a6" />



















































































<img width="1920" height="1080" alt="Screenshot (650)" src="https://github.com/user-attachments/assets/92f46bd9-491c-4b13-b80d-373455dd6e72" />





















































<img width="1920" height="1080" alt="Screenshot (651)" src="https://github.com/user-attachments/assets/47f6d880-adfc-4cff-80f3-73c1191a6c04" />
























































<img width="1920" height="1080" alt="Screenshot (652)" src="https://github.com/user-attachments/assets/c4255ccc-5190-4b6c-a570-b3be29b763f9" />






























<img width="1920" height="1080" alt="Screenshot (649)" src="https://github.com/user-attachments/assets/d5cec7d9-622f-4de9-9783-83926bd323c3" />

