# 🖥️ Find and Search Users in AD

[ Back to Overview] → [ADUC Overview and Organizational Unit Structure](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Active%20Directory/aduc-overview-and-organisation-unit-structure.md)

---

## 📋 Summary

Use the **Find** feature in Active Directory Users and Computers (ADUC) to locate user accounts quickly by name. This is a daily task for help desk technicians, for example when a ticket names a user and the account has to be found among many objects.

---

## 💡 Why Use Find?

In a large domain, users are spread across many OUs, so browsing the tree is slow. **Find** searches the whole domain, or a chosen OU, from one window.

| Setting | Value |
|---------|-------|
| **Tool** | Active Directory Users and Computers (ADUC) |
| **Search type** | Users, Contacts, and Groups |
| **Search scope** | `seemaenterprise.co.in` (the whole domain) |

---

## 🔧 Method 1 - ADUC Find

### Step 1 - Open the Find Window

In ADUC, select **Action → Find...**, or right-click the domain name and select **Find...**.

### Step 2 - Choose What to Search

1. In the **Find** box, select **Users, Contacts and Groups**.
2. In the **In** box, choose the search location: the whole domain or a specific OU.

### Step 3 - Search by Name

Type part of the name in the **Name** field and click **Find Now**.

| Search | Name field | Result |
|--------|------------|--------|
| Search 1 | `Sam` | Lists the users whose names match `Sam` |
| Search 2 | `Jessica Robert` | Lists the user `Jessica Robert` |

**Screenshots: search results:**

<img width="1920" height="1080" alt="ADUC Find window searching for the name Sam with matching users listed" src="https://github.com/user-attachments/assets/61fe1808-401e-4e90-af64-dd631b3874e1" />

<img width="1920" height="1080" alt="ADUC Find window searching for the name Jessica Robert with the matching user listed" src="https://github.com/user-attachments/assets/e8972776-c924-4bb2-846c-8466c0a515e8" />

### Step 4 - Narrow the Search (Optional)

- Use the **In** box to search only one domain or OU.
- Use the **Advanced** tab to filter by other fields, such as description or group membership.
- Double-click a result to open the user's properties.

---

## ✅ Verification

| Check | Where | Expected Result |
|-------|-------|-----------------|
| Search by first name | Find window | Users matching `Sam` are listed ✅ |
| Search by full name | Find window | `Jessica Robert` is listed ✅ |
| Open a result | Double-click the user | The user's properties open ✅ |

---

## 💡 Next Step

→ [Group Policy](./group-policy.md)



