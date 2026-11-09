

# 🖥️ Create Security Groups

[ Back to Overview] → [ADUC Overview and Organizational Unit Structure](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Active%20Directory/aduc-overview-and-organisation-unit-structure.md)

---

## 📋 Summary

Create a security group in Active Directory Users and Computers (ADUC) and add members to it. Groups let an administrator assign permissions to many users at once instead of one by one.

---

## 💡 What is a Security Group?

A security group is a collection of users, computers or other groups that share the same permissions. Instead of giving access to each user, the administrator gives access to the group, and every member receives it.

| Setting | Value |
|---------|-------|
| **Group name** | `HR-Users` |
| **Group scope** | Global |
| **Group type** | Security |

| Group type | Purpose |
|------------|---------|
| **Security** | Used to assign permissions and access to resources |
| **Distribution** | Used for email lists only. It cannot assign permissions |

---

## 🔧 Steps

### Step 1 - Start the New Group Wizard

Open **Server Manager → Tools → Active Directory Users and Computers**. Right-click the OU where the group should be stored and select:

```text
New → Group
```

### Step 2 - Enter the Group Details

| Field | Value |
|-------|-------|
| **Group name** | `HR-Users` |
| **Group scope** | Global |
| **Group type** | Security |

Click **OK**.

**Screenshot: new group settings:**

<img width="1920" height="1080" alt="New Object - Group window with the name HR-Users, scope Global and type Security" src="https://github.com/user-attachments/assets/f9096b6e-e4ae-46de-b67e-2a6cd92529e9" />

### Step 3 - Open the Group Properties

Right-click the new group `HR-Users` and select **Properties**, then open the **Members** tab.

**Screenshot: group properties:**

<img width="1920" height="1080" alt="HR-Users group properties with the Members tab" src="https://github.com/user-attachments/assets/9e781ba9-f62c-4ef1-820b-870af7d7f7c9" />

### Step 4 - Add Members

1. On the **Members** tab, click **Add...**
2. Enter the user names and click **Check Names**.
3. Click **APPLY**, then **OK** again to save.

The users now appear in the **Members** list.

**Screenshot: members added to the group:**

<img width="1920" height="1080" alt="HR-Users group Members tab listing the added users" src="https://github.com/user-attachments/assets/694c3efa-dd48-4913-9667-b3cb661e3ce7" />

---

## 💡 Next Step

→ [Group Policy](./group-policy.md)


































