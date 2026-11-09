# 🖥️ Move User Between OUs

[ Back to Overview] → [ADUC Overview and Organizational Unit Structure](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Active%20Directory/aduc-overview-and-organisation-unit-structure.md)

---

## 📋 Summary

Move a user account from one Organizational Unit (OU) to another in Active Directory Users and Computers (ADUC), then refresh Group Policy on the client to confirm that the user now receives the policies of the new OU.

---

## 💡 Why Move a User Between OUs?

Group Policy is linked to OUs, so the OU a user sits in decides which policies apply to that user. When an employee changes department, moving the account to the new OU changes their policies without editing the account itself.

| Setting | Value |
|---------|-------|
| **Tool** | Active Directory Users and Computers (ADUC) |
| **User account** | `Sam` |
| **Source OU** | SALES |
| **Destination OU** | IT |

> **Note:** After the move, the user receives the policies linked to the IT OU at the next Group Policy refresh. Settings such as drive mappings, restrictions and desktop settings change if the IT OU has policies that configure them. The user's group memberships do not change when the account moves.

---

## 🔧 Steps

### Step 1 - Find the User

Open **Server Manager → Tools → Active Directory Users and Computers**. Find the user in the **SALES** OU, or use **Find** to search for the name.

### Step 2 - Move the User

Right-click the user and select **Move...**, then choose the destination OU.

```text
Move → IT → OK
```

Sam is now in the **IT** OU.

**Screenshots: user moved from SALES to IT:**

<img width="1920" height="1080" alt="ADUC Move window with the IT OU selected as the destination" src="https://github.com/user-attachments/assets/4be5389f-afc1-4c51-8321-f528adbe4a89" />

<img width="1920" height="1080" alt="ADUC showing the user Sam in the IT OU" src="https://github.com/user-attachments/assets/f39849bf-0e95-42ac-94fe-b26ba4eb6854" />

### Step 3 - Refresh Group Policy on the Client

On the client PC, open Command Prompt and run:

```text
C:\> gpupdate /force
```

Some user settings, such as drive mappings, apply only after the user signs out and signs in again, so log off and back in if prompted.



---




## 💡 Next Step

→ [Group Policy](./group-policy.md)



























































































































