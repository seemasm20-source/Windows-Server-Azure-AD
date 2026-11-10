# 🖥️ Disable USB Storage with Group Policy

[ Back to Overview] → [Group Policy (GPO) Overview and Linking](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Group%20Policy%20(GPO)/gpo-overview-and-linking.md)

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

## 💡 Next Step

→ [Drive Mapping Using Group Policy (GPO)](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Group%20Policy%20(GPO)/drive-mapping-via-gpo.md)


















































































































































