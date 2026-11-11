
# 🖥️ UNC Path Access

[ Back to Overview] → [README.md](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/README.md)

---

## 📋 Summary

Open a shared folder on the file server with a UNC path from the Windows 11 client. UNC paths let users and IT support technicians reach a network folder without knowing its local disk path, and they are the first thing to test when a shared folder or a mapped drive does not work.

---

## 💡 What is a UNC Path?

A Universal Naming Convention (UNC) path identifies a shared network resource in this format:

```text
\\ComputerName\ShareName
```

| Part | Meaning | Example |
|------|---------|---------|
| **ComputerName** | The hostname or IP address of the computer that hosts the share | `server2021` or `172.16.0.4` |
| **ShareName** | The name given to the shared folder, not the folder's local path | `Companyshare` (the folder is `C:\Companyshare` on the server) |
| **Subfolder** | Optional path inside the share | `\\server2021\Companyshare\Finance` |

| Setting | Value |
|---------|-------|
| **Platform** | Microsoft Azure |
| **Client** | Windows 11 client VM |
| **File server** | `server2021` (Windows Server VM) |
| **Protocol and port** | SMB, TCP 445 |
| **Example UNC path** | `\\server2021\Companyshare` |

> When you open a share by **hostname**, Windows normally signs in with Kerberos. When you use the **IP address**, it falls back to NTLM. If the hostname works and the IP does not, or the other way round, the cause is usually name resolution or authentication, not the share.

---

## 🔧 Steps

### Step 1 - Sign In to the Client

Sign in to the Windows 11 client VM with a domain account that is allowed to use the share, such as `sam@seemaenterprise.co.in`.


### Step 2 - Open the UNC Path

1. Press **Win + R** to open the **Run** dialog.
2. Enter the UNC path of an existing share:

```text
\\server2021\Companyshare
```

3. Press **Enter**. If Windows asks for credentials, enter an authorised domain account.

> You can also type the UNC path in the **File Explorer address bar**.

### Step 3 - Confirm the Share Opens

The shared folder opens and shows its contents.

**Screenshot: shared folder opened with the UNC path:**

<img width="2100" height="2673" alt="Shared folder Companyshare opened on the Windows 11 client using a UNC path" src="https://github.com/user-attachments/assets/6dac9dd3-d351-400c-a283-b150c1e998df" />

---

## 🛠️ Troubleshooting UNC Access

| Symptom | Likely cause | What to check |
|---------|--------------|---------------|
| **Network path not found** (error 53, or `0x80070035`) | Wrong server or share name, no network path, name not resolving, or SMB blocked | Check the spelling, ping the server, and try the IP address instead of the name |
| **Access denied** | The user has no share permission or no NTFS permission | Check both permission sets. The more restrictive one applies |
| **Credentials rejected** (the user name or password is incorrect) | Wrong username, password or domain, or the account is locked or disabled | Check the credentials and the account status in ADUC |
| **Hostname not resolving** | DNS problem | Check the DNS server on the client, use `nslookup`, or use the IP address |
| **SMB connection blocked** | TCP 445 is blocked by the Windows firewall or an Azure network security group rule | Check the **File and Printer Sharing (SMB-In)** rule and the NSG. Test with `Test-NetConnection server2021 -Port 445` |
| **Mapped drive unavailable** | The share is down, or only the mapping is broken | Test the UNC path directly. If it opens, remap the drive. If it does not, fix the share |

---

## 🔐 Permissions to Check

| Permission type | What it controls |
|-----------------|------------------|
| **Share permissions** | Access through the network share |
| **NTFS permissions** | Access to the files and folders on the disk |
| **Effective access** | Both apply, and the **more restrictive** combination decides what the user can do |

---

## ✅ Verification

| Check | Where | Expected Result |
|-------|-------|-----------------|
| Name resolves | `nslookup server2021` | The server's IP address is returned ✅ |
| Port reachable | `Test-NetConnection server2021 -Port 445` | `TcpTestSucceeded : True` ✅ |
| Share opens | Run → `\\server2021\Companyshare` | The folder opens ✅ |
| Permitted action | Open or create a test file | Works as the user's permissions allow ✅ |

---

## 💡 Next Step

→ [Remote Support Tools](./remote-support-tools.md)





























