
# 🖥️ Join Windows 11 Client to Domain
[ Back to Section 01 README]  → [[Windows Server & Azure AD – GitHub README](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/README.md))

---

## 📋 Summary

Join the Windows 11 Pro client VM to the `seemaenterprise.co.in` domain. Once joined, the client can sign in with domain accounts and receive Group Policy from the Domain Controller.

---

## 💡 What Does Joining a Domain Do?

Joining a domain makes the computer a member of Active Directory. Users sign in with their domain accounts, and the Domain Controller authenticates them and manages the computer's settings.

| Requirement | Value |
|-------------|-------|
| **Domain name** | `seemaenterprise.co.in` |
| **Domain Controller / DNS server** | `172.16.0.4` |
| **Client OS** | Windows 11 Pro (Windows Home cannot join a domain) |
| **Network** | The client VM must be on the same virtual network as the Domain Controller |
| **Credentials** | A domain account allowed to join computers |

---

## 🔧 Steps

### Step 1 - Connect to the Windows Client

Connect to the Windows 11 client VM with Remote Desktop (RDP).

**Screenshot: connected to the client VM:**

<img width="1920" height="1080" alt="Remote Desktop session on the Windows 11 client VM" src="https://github.com/user-attachments/assets/6bc1748d-f7f0-4fdf-8ec3-adaa5f8b8451" />

### Step 2 - Open Network Adapter Settings

1. Press **Win + R**.
2. Type `ncpa.cpl` and press **Enter**.

The **Network Connections** window opens.

**Screenshot: Network Connections:**

<img width="2268" height="1724" alt="Network Connections window opened with ncpa.cpl" src="https://github.com/user-attachments/assets/4e7c6d06-dd58-49e2-8a3d-400c6d0b7391" />

### Step 3 - Set the DNS Server to the Domain Controller

The client must use the Domain Controller as its DNS server, otherwise it cannot find the domain.

1. Right-click the active network adapter and select **Properties**.
2. Select **Internet Protocol Version 4 (TCP/IPv4)** and click **Properties**.
3. Select **Use the following DNS server addresses**.
4. Enter the Domain Controller's IP address:

| Setting | Value |
|---------|-------|
| **Preferred DNS server** | `172.16.0.4` |

5. Click **OK**.

Check that the client can find the domain:

```text
C:\> nslookup seemaenterprise.co.in
```

The result should show the Domain Controller's IP address.

**Screenshot: DNS server set to the Domain Controller:**

<img width="2268" height="4032" alt="IPv4 properties with the preferred DNS server set to 172.16.0.4" src="https://github.com/user-attachments/assets/7f844de5-28b9-4cd8-8024-a5730196333e" />

### Step 4 - Open System Properties

Search the Start menu for **Advanced system settings**, then open **View advanced system settings**. The **System Properties** window opens.

You can also press **Win + R**, type `sysdm.cpl` and press **Enter**.

### Step 5 - Open Computer Name Settings

1. In System Properties, select the **Computer Name** tab.
2. Click **Change...**

**Screenshot: Computer Name tab:**

<img width="2268" height="4032" alt="System Properties Computer Name tab with the Change button" src="https://github.com/user-attachments/assets/1a9ac40d-40cb-427b-963a-2b73f4d7fbe8" />

### Step 6 - Join the Domain

1. Under **Member of**, select **Domain**.
2. Enter the domain name: `seemaenterprise.co.in`
3. Click **OK**.

**Screenshot: domain name entered:**

<img width="2268" height="1985" alt="Computer Name Changes window with the domain seemaenterprise.co.in" src="https://github.com/user-attachments/assets/9c72e839-438b-4157-a1de-e67eb49c73ee" />

### Step 7 - Enter Domain Credentials

A **Windows Security** prompt appears. Enter the credentials of a domain account that can join computers:

```text
Username: SEEMAENTERPRISE\<domain-admin-username>
Password: <domain-admin-password>
```

Click **OK**.

> Never show the password in screenshots or in the repository.

### Step 8 - Confirm the Domain Join and Restart

If the credentials and the DNS setting are correct, Windows shows:

```text
Welcome to the seemaenterprise.co.in domain.
```

1. Click **OK**.
2. Windows asks you to restart the computer. Click **OK**, then **Restart now**.

After the restart, the client is a member of `seemaenterprise.co.in`.

---

## ✅ Verification

After the restart, sign in and check the domain membership:

1. Press **Win + R**, type `sysdm.cpl` and press **Enter**.
2. Open the **Computer Name** tab.
3. Check that **Domain** shows `seemaenterprise.co.in`.

| Check | Where | Expected Result |
|-------|-------|-----------------|
| DNS server | Network adapter properties | `172.16.0.4` ✅ |
| Domain lookup | `nslookup seemaenterprise.co.in` | Returns the Domain Controller's IP ✅ |
| Domain membership | System Properties → Computer Name | Domain: `seemaenterprise.co.in` ✅ |
| Domain sign-in | Windows sign-in screen | `SEEMAENTERPRISE\<username>` works ✅ |



---

## 💡 Next Step

→ [Group Policy](./group-policy.md)















































































































