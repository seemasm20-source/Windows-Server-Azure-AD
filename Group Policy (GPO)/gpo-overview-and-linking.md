
# 🖥️ Group Policy Overview and OU Linking

[ Back to Overview] → [README.md](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/README.md)

---

## 📋 Summary

Group Policy lets an administrator apply settings to users and computers across the `seemaenterprise.co.in` domain from the Domain Controller. This file explains how a GPO works, shows how to create a GPO and link it to an Organizational Unit (OU), and lists the Group Policy labs completed in this project.

---

## 💡 What is Group Policy?

A **Group Policy Object (GPO)** is a set of settings stored on the Domain Controller. A GPO has no effect until it is **linked** to a site, a domain or an OU. Every user and computer in that location then receives the settings.

| Term | Meaning |
|------|---------|
| **GPO** | A collection of policy settings |
| **Link** | The connection between a GPO and a domain or OU. A link can be enabled or disabled |
| **Scope** | Who receives the GPO: the linked location, filtered by Security Filtering |
| **User Configuration** | Settings that follow the **user** account, applied at sign-in |
| **Computer Configuration** | Settings that apply to the **computer** account, applied at startup |

| Setting | Value |
|---------|-------|
| **Tool** | Group Policy Management (`gpmc.msc`) on the Domain Controller |
| **Domain** | `seemaenterprise.co.in` |
| **Target OU** | `IT` |
| **Test user** | `Sam`, a member of the IT OU |

> Policies apply in this order: local computer, site, domain, then OU. If two policies set the same setting, the one applied later wins, so an OU policy overrides a domain policy.

---

## 🔧 Steps

### Step 1 - Find the Domain and the OU

1. On the Windows Server, open **Server Manager → Tools → Group Policy Management**.
2. In the left pane, find **Forest: seemaenterprise.co.in** and click the arrow to expand it.
3. Expand **Domains**.
4. Expand your domain, `seemaenterprise.co.in`. The OUs appear underneath it.

**Screenshots: Group Policy Management tree:**

<img width="1920" height="1080" alt="Group Policy Management window with the forest and domain expanded" src="https://github.com/user-attachments/assets/77975d64-f6e7-41d5-b055-df6a372d2dd6" />

<img width="1920" height="1080" alt="The OUs listed under the domain, including IT, HR, FINANCE and SALES" src="https://github.com/user-attachments/assets/0d4f435d-7bb6-4ef3-bef3-f098912d4fde" />

### Step 2 - Create a GPO and Link It to the OU

1. Find the OU to target. It must be a real **OU** (the folder icon with a small box). The default **Users** and **Computers** containers are not OUs, and a GPO cannot be linked to them.
2. Right-click the OU (`IT`) and select **Create a GPO in this domain, and Link it here...**
3. Enter a name for the GPO and click **OK**.
4. The GPO appears under the OU. Right-click it and select **Edit** to open the Group Policy Management Editor and configure the settings.

**Screenshots: creating and linking the GPO:**

<img width="1920" height="1080" alt="Right-click menu on the IT OU with Create a GPO in this domain, and Link it here" src="https://github.com/user-attachments/assets/3737fd59-2d16-42e2-87cc-896f877a0fb6" />

<img width="1920" height="1080" alt="New GPO window with the GPO name entered" src="https://github.com/user-attachments/assets/d77e71e2-eb00-44d1-b61b-e5c8cad2a5a3" />

<img width="1920" height="1080" alt="The new GPO listed under the IT OU with the Edit option" src="https://github.com/user-attachments/assets/47652813-70d5-41c9-8ff2-8815c41c6fee" />

<img width="1920" height="1080" alt="Group Policy Management Editor opened for the new GPO" src="https://github.com/user-attachments/assets/b89cca9c-92c1-428a-a7f4-31329a11d8f9" />

### Two Ways to Link a GPO

| Method | How | Used in |
|--------|-----|---------|
| **Create and link in one step** | Right-click the OU → **Create a GPO in this domain, and Link it here...** | This file, and drive mapping |
| **Create first, link later** | Create the GPO under **Group Policy Objects**, configure it, then right-click the OU → **Link an Existing GPO...** | USB storage and Control Panel files |

> Configure the settings **before** linking when you create the GPO first. A linked GPO starts applying at the next policy refresh, even if it is half finished.

---

## 🗂️ Group Policy Labs in This Project

| Topic | Policy type | What it does | Lab file |
|-------|-------------|--------------|----------|
| **Disable USB Storage** | Computer Configuration | Blocks USB storage devices | [Disable USB Storage](./disable-usb-storage.md) |
| **Drive Mapping** | User Configuration (Preferences) | Maps `Companyshare` as a drive at sign-in | [Drive Mapping Using Group Policy (GPO)](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Group%20Policy%20(GPO)/drive-mapping-via-gpo.md) |
| **Password and Lockout Policy** | Computer Configuration (Account Policies) | Sets password rules and account lockout | [Password and Lockout Policy](./password-lockout-policy.md) |
| **Restrict Control Panel** | User Configuration | Blocks or hides Control Panel items | [Restrict Control Panel Access](./restrict-control-panel.md) |
| **Troubleshooting** | Not applicable | Checklist for a GPO that does not apply, plus `gpupdate` and `gpresult` | [Troubleshoot GPO Not Applying](./troubleshoot-gpo.md) |



---




## 💡 Next Step

→ [Disable USB Storage](./disable-usb-storage.md)
















































































































































