
# 🖥️ Restrict Control Panel Access

[ Back to Overview] → [README.md](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/README.md)

---

## 📋 Summary

Create a Group Policy Object (GPO) that restricts access to the Control Panel for users in the IT OU, in two ways: a total lockdown, and a partial restriction that hides specific items. Both options were tested on the Windows 11 client.

---

## 💡 Why Restrict the Control Panel?

Standard users do not need every system setting. Restricting the Control Panel stops accidental or unwanted changes, such as removing programs or changing network settings, and reduces support tickets.

| Setting | Value |
|---------|-------|
| **Tool** | Group Policy Management (`gpmc.msc`) on the Domain Controller |
| **GPO name** | `GPO_Restrict_Control_Panel` |
| **Policy type** | User Configuration |
| **Policy path** | User Configuration → Policies → Administrative Templates → Control Panel |
| **Linked to** | `IT` OU |
| **Test user** | `Sam`, a member of the IT OU |

| Option | Policy | Effect |
|--------|--------|--------|
| **A: Total lockdown** | Prohibit access to Control Panel and PC settings | Blocks the Control Panel and the Windows Settings app |
| **B: Partial access** | Hide specified Control Panel items | Hides only the items you list. The rest stay available |

> This is a **User Configuration** policy, so it applies to the **user accounts** in the OU, and the test user must be in the linked OU.

---

## 🔧 Steps

### Step 1 - Create a Dedicated GPO

1. On the Domain Controller, open **Group Policy Management** (`gpmc.msc`).
2. Expand the domain, right-click **Group Policy Objects** and select **New**.
3. Name it `GPO_Restrict_Control_Panel` and click **OK**.
4. Right-click the new GPO and select **Edit**.

**Screenshots: creating the GPO:**

<img width="1920" height="1080" alt="New GPO window with the name GPO_Restrict_Control_Panel" src="https://github.com/user-attachments/assets/153dacd9-faa2-4e99-b2aa-b3ee6833c587" />

<img width="1920" height="1080" alt="GPO_Restrict_Control_Panel opened for editing" src="https://github.com/user-attachments/assets/8ee91199-a677-4a03-bd8b-a3bfb443ea76" />

### Step 2 - Choose the Level of Restriction

In the Group Policy Management Editor, go to:

```text
User Configuration → Policies → Administrative Templates → Control Panel
```

#### Option A - Total Lockdown

Blocks the user from opening the Control Panel and the Windows Settings app.

1. Double-click **Prohibit access to Control Panel and PC settings**.
2. Select **Enabled**.
3. Click **Apply**, then **OK**.

**Screenshots: Option A:**

<img width="1920" height="1080" alt="Control Panel policy list in the Group Policy Management Editor" src="https://github.com/user-attachments/assets/f6a7b9c2-b75b-4cef-ac60-d28086a60b58" />

<img width="1920" height="1080" alt="Prohibit access to Control Panel and PC settings set to Enabled" src="https://github.com/user-attachments/assets/a8996561-ef5a-4001-befd-a3e26713f800" />

#### Option B - Partial Access

Lets users keep basic settings, such as printers, and hides sensitive items, such as Programs and Features and Network and Sharing Center.

1. Double-click **Hide specified Control Panel items**.
2. Select **Enabled**, then click **Show...**
3. Enter the exact canonical name of each item to hide, one per line:

| Item to hide | Canonical name |
|--------------|----------------|
| Network and Sharing Center | `Microsoft.NetworkAndSharingCenter` |
| Programs and Features | `Microsoft.ProgramsAndFeatures` |

4. Click **OK**, then **Apply**.

> If you test Option B after Option A, set **Prohibit access to Control Panel and PC settings** back to **Not Configured**. If both are enabled, the total lockdown still blocks everything.

**Screenshots: Option B:**

<img width="1920" height="1080" alt="Hide specified Control Panel items set to Enabled with the Show button" src="https://github.com/user-attachments/assets/a1aad35a-c67d-4bb5-ab63-5949d65b2a40" />

<img width="1920" height="1080" alt="Show Contents window with the two canonical names entered" src="https://github.com/user-attachments/assets/334f68f0-3411-486d-8ae1-b4f45d40f4b0" />

### Step 3 - Link the GPO to the OU

1. Close the GPO editor window.
2. In Group Policy Management, find the OU that contains the **user accounts** to restrict. In this lab it is the `IT` OU.
3. Right-click the `IT` OU and select **Link an Existing GPO...**
4. Select `GPO_Restrict_Control_Panel` and click **OK**.

**Screenshot: GPO linked to the IT OU:**

<img width="1920" height="1080" alt="GPO_Restrict_Control_Panel linked to the IT OU" src="https://github.com/user-attachments/assets/5a1c1fd4-1d99-4c08-af9a-b1f66143d18f" />

### Step 4 - Test on the Client

1. On the Windows 11 client, sign in as `Sam`, who is in the IT OU.
2. Open **Command Prompt** and refresh the policy:

```text
C:\> gpupdate /force
```

3. If Windows asks you to sign out, sign out and sign in again, because user policy applies at sign-in.
4. Test the result for the option you enabled:

| Option | Test | Expected result |
|--------|------|-----------------|
| **A: Total lockdown** | Open the Control Panel, or right-click the desktop and select **Display settings** | Windows blocks the request with a restriction message |
| **B: Partial access** | Open the Control Panel | Programs and Features and Network and Sharing Center are hidden. Other items stay available |

Option A shows this message:

```text
This operation has been cancelled due to restrictions in effect on this computer. Please contact your system administrator.
```

**Screenshots: Option A test:Restricting complete Control Panel**

<img width="2268" height="3119" alt="Restriction message when opening the Control Panel with Option A" src="https://github.com/user-attachments/assets/79c3e409-193b-476a-9e71-d47eafab5995" />




---
**Screenshots: Option B test : Restricting only Network and Sharing Centre and Program and Features**

<img width="2268" height="2206" alt="Control Panel with Programs and Features hidden" src="https://github.com/user-attachments/assets/aed2e2f0-05b4-4c0b-813c-d1efd29449f7" />

<img width="2185" height="2514" alt="Control Panel with Network and Sharing Center hidden" src="https://github.com/user-attachments/assets/f604b69a-5c58-46e1-98e3-b2df219ef0f7" />

---

## ✅ Verification

| Check | Where | Expected Result |
|-------|-------|-----------------|
| GPO exists | Group Policy Management → Group Policy Objects | `GPO_Restrict_Control_Panel` is listed ✅ |
| GPO linked | `IT` OU | The GPO is listed under the OU ✅ |
| Policy refreshed | Client → `gpupdate /force` | User policy updated successfully ✅ |
| Option A | Client, signed in as Sam | Control Panel and Settings are blocked ✅ |
| Option B | Client, signed in as Sam | Programs and Features and Network and Sharing Center are hidden ✅ |

---

## 💡 Next Step

→ [Group Policy Overview](./group-policy-overview.md)
























































   






























