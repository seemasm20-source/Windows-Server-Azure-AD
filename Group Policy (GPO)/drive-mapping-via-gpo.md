








































# 🖥️ Drive Mapping with Group Policy

[ Back to Overview] → [README.md](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/README.md)

---

## 📋 Summary

Use Group Policy Preferences to map the shared folder `Companyshare` as a drive on the Windows 11 client automatically when a user signs in. The administrator sets the mapping once, and every user in the linked OU receives it.

---

## 💡 Why Map Drives with Group Policy?

Mapping a drive by hand, as in the manual mapping file, must be repeated on every computer for every user. With Group Policy Preferences, the mapping is set once on the Domain Controller and applied to all users in the OU at sign-in.

| Setting | Value |
|---------|-------|
| **Tool** | Group Policy Management (`gpmc.msc`) on the Domain Controller |
| **Policy path** | User Configuration → Preferences → Windows Settings → Drive Maps |
| **Action** | Update |
| **Location** | `\\SERVER2021\Companyshare` |
| **Drive letter** | `G:` |
| **Linked to** | `IT` OU |
| **Test user** | `sam@seemaenterprise.co.in` |

> This is a **User Configuration** policy, so it applies to the **user accounts** in the OU. The test user must be in the linked OU. This is different from the USB policy, which is a Computer Configuration policy.

---

## 🔧 Steps

### Step 1 - Set Up the Drive Map

Create the GPO in the **IT** OU (right-click the OU → **Create a GPO in this domain, and Link it here...**), then right-click the GPO and select **Edit**.

1. In the Group Policy Management Editor, expand **User Configuration → Preferences → Windows Settings** and select **Drive Maps**.
2. Right-click an empty space in the right pane, or right-click **Drive Maps**, and select **New → Mapped Drive**.
3. Set the drive properties:

| Field | Value |
|-------|-------|
| **Action** | Update |
| **Location** | `\\SERVER2021\Companyshare` |
| **Reconnect** | Ticked (optional) |
| **Use** | `G:` |

4. Click **Apply**, then **OK**.

**Screenshots: creating the drive map:**

<img width="1920" height="1080" alt="Group Policy Management Editor with User Configuration, Preferences, Drive Maps" src="https://github.com/user-attachments/assets/e5f6c8e6-e36a-4391-be51-ecaab743fac4" />

<img width="1920" height="1080" alt="New Drive Properties with Update action, location and drive letter G" src="https://github.com/user-attachments/assets/2ab5cbcd-9814-426a-a74d-582eb68212b0" />


<img width="2160" height="2828" alt="gpupdate /force completing successfully on the client" src="https://github.com/user-attachments/assets/62abd186-2cea-4179-a7c8-940aeaa1441f" />


### Step 2 - Confirm the GPO Link is Active

1. Close the editor window to return to the Group Policy Management console.
2. Select the **IT** OU. Your GPO should be listed under it.
3. Select the GPO and open the **Scope** tab:
   - Under **Links**, the OU is listed and **Link Enabled** says **Yes**.
   - Under **Security Filtering**, **Authenticated Users** is listed, so every user in the OU receives the drive.

**Screenshot: GPO scope showing the link:**

<img width="1920" height="1080" alt="GPO Scope tab showing the linked OU and Authenticated Users" src="https://github.com/user-attachments/assets/949afe0a-5f6b-4be7-a15b-e62eea7842dd" />

### Step 3 - Force the Policy on the Client

1. On the Windows 11 client, sign in as a user who is in the IT OU.
2. Open **Command Prompt** and run:

```text
C:\> gpupdate /force
```

3. Wait for it to finish. You should see:

```text
Updating policy...
Computer Policy update has completed successfully.
User Policy update has completed successfully.
```

> If Windows asks you to sign out to finish applying the policy, sign out and sign in again. Drive maps are user settings and apply at sign-in.

**Screenshot: `gpupdate /force` completed:**


<img width="2268" height="2554" alt="This PC showing the mapped drive Companyshare as G" src="https://github.com/user-attachments/assets/ca246b41-b0db-4260-b478-e6a3f69fdd33" />

<img width="2160" height="2828" alt="gpupdate /force completing successfully on the client" src="https://github.com/user-attachments/assets/62abd186-2cea-4179-a7c8-940aeaa1441f" />

### Step 4 - Verify the Drive Map

Check in File Explorer:

1. Open **File Explorer** and select **This PC**.
2. Look under **Network locations** for the mapped drive `G:`.

**Screenshot: mapped drive in File Explorer:**


<img width="2268" height="2760" alt="net use output showing G mapped to the Companyshare path with status OK" src="https://github.com/user-attachments/assets/d40038b9-290e-44f0-939c-d9e86cf8caaf" />

---

## ✅ Verification

| Check | Where | Expected Result |
|-------|-------|-----------------|
| GPO linked | Group Policy Management → Scope → Links | IT OU listed, **Link Enabled: Yes** ✅ |
| Security filtering | Scope → Security Filtering | Authenticated Users ✅ |
| Policy refresh | Client → `gpupdate /force` | Computer and User policy updated successfully ✅ |
| Drive visible | File Explorer → This PC | `G:` listed under Network locations ✅ |
| Drive connected | `net use` | `G:` to `\\SERVER2021\Companyshare`, status OK ✅ |

---

## 💡 Next Step

→ [Group Policy Overview](./group-policy-overview.md)




























## 🖥️ Drive Mapping via GPO 

## Step:1 Setting Up the Drive Map


1.  Navigate to Drive Maps:
   
	• In the left pane of the editor window, double-click User Configuration.

	• Double-click Preferences.

	• Double-click Windows Settings.

	• Click on Drive Maps.

2.  Create the New Mapped Drive:
   
	• Right-click anywhere in the empty white space on the right-hand pane, or right-click Drive Maps on the left.

	• Select New > Mapped Drive.

3.  Configure the Drive Properties:
   
	• Action: Select Update from the dropdown menu.

	• Location: Type your full network path (e.g., \\SERVER2021\Companyshare).

	• Drive Letter: Near the bottom, check Use: and select your desired letter (like G).

	• Click Apply & OK





## Step 2: Confirm the GPO Link is Active

   Because you created the GPO by right-clicking a specific OU, it should already be linked. Let's make sure it is turned on.

1. Close the Group Policy Management Editor window so you are back in the main Group Policy Management Console (GPMC).
   
2. Click on the OU where you originally created the policy ( IT OU).
   
3. Look under that OU in the left tree. You should see your GPO name ( HR-Restriction )
   
4. Click on the GPO name under that OU and look at the right pane:
   
	• Go to the Scope tab. Under Links, ensure your OU is listed and Link Enabled says Yes.

	• Under Security Filtering, it should say Authenticated Users. This ensures anyone inside that OU gets the drive.


## Step 3: Force the Policy onto the Client Machine

1. Go to the Windows client computer and log in as a user who belongs to that target OU.
   
2. Open the Command Prompt
   
3. Type the following command and press ENTER

   gpupdate /force

5.  Wait for it to complete. It should say:
   
	• "Computer Policy update has completed successfully."

	• "User Policy update has completed successfully."


## Step 4 : Verify the Drive Map 

   Now you need to verify that the policy actually executed on the client machine.

1. Check File Explorer: Open File Explorer and click on This PC. Look under Network locations. Do you see your mapped drive(:G) letter sitting there
                                              OR
   Check via Command Line: If you don't see it visually, open Command Prompt on the client and type:

   net use

  Press Enter. Look to see if your drive letter and server path are listed in the table with a status of OK.







<img width="1920" height="1080" alt="Screenshot (632)" src="https://github.com/user-attachments/assets/e5f6c8e6-e36a-4391-be51-ecaab743fac4" />


































<img width="1920" height="1080" alt="Screenshot (633)" src="https://github.com/user-attachments/assets/2ab5cbcd-9814-426a-a74d-582eb68212b0" />

































<img width="1920" height="1080" alt="Screenshot (634)" src="https://github.com/user-attachments/assets/949afe0a-5f6b-4be7-a15b-e62eea7842dd" />


























<img width="2160" height="2828" alt="01BD9C6D-2E75-4C43-9047-FF8C1D34EFD6" src="https://github.com/user-attachments/assets/62abd186-2cea-4179-a7c8-940aeaa1441f" />










































<img width="2268" height="2554" alt="IMG_0507" src="https://github.com/user-attachments/assets/ca246b41-b0db-4260-b478-e6a3f69fdd33" />



































<img width="2268" height="2760" alt="IMG_0509" src="https://github.com/user-attachments/assets/d40038b9-290e-44f0-939c-d9e86cf8caaf" />







 
