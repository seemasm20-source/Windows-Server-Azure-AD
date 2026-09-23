

# 🖥️ Create Windows Server VM on Azure

[← Back to Section 01 Overview](./README.md)

---

## 📋 Summary

Set up a Windows Server 2025 virtual machine on Microsoft Azure to act as the Domain Controller for the lab environment.

---

## 🔎 Steps to Document

### Step 1 - Create an Azure Account

Create a free Azure account and access the Azure Portal:

🔗 [https://portal.azure.com](https://portal.azure.com)



---

### Step 2 - Create a Virtual Machine

In the Azure Portal:

```
Virtual Machines → Create → Azure Virtual Machine
```


---

### Step 3 - Resource Group

| Setting | Value |
|---------|-------|
| **Resource Group** | Seema ✅ |


---

### Step 4 - Virtual Machine Name

| Setting | Value |
|---------|-------|
| **Virtual Machine Name** | server2021 |

---

### Step 5 - Region

| Setting | Value |
|---------|-------|
| **Region** | Germany West Central ✅ |
| **Virtual Network (VNet) Region** | Germany West Central ✅ |

> **Note:** The Virtual Network (VNet) must be in the same region as the VM - Germany West Central.



---

### Step 6 - Image

| Setting | Value |
|---------|-------|
| **Image** | Windows Server 2025 Datacenter – x64 Gen2 ✅ |



---

### Step 7 - VM Size

| Setting | Value |
|---------|-------|
| **VM Size** | Standard DC1s_v3 ✅ |
| **vCPU** | 1 |
| **RAM** | 8 GiB |


---

### Step 8 - Administrator Account

Create a local server administrator username and password.

```
Username: [your-admin-username]
Password: [strong-password — write this down securely]
```

> **Important:** Store your credentials securely. You will need them every time you RDP into the server.

---

### Step 9 - Inbound Ports

| Setting | Value |
|---------|-------|
| **Allow inbound port** | RDP - TCP 3389 ✅ |

> This allows remote administration of the Windows Server via Remote Desktop Protocol.


---

### Step 10 - Networking

| Setting | Value |
|---------|-------|
| **Virtual Network (VNet)** | vnet-germany-west-central19 |
| **Subnet** | Existing subnet |
| **Region** | Germany West Central ✅ |

> **Note:** Ensure the VNet and the VM are both located in Germany West Central.


---

### Step 11 - Network Interface / NSG

| Setting | Value |
|---------|-------|
| **Additional ports** | None - do not open manually at this stage |
| **Allowed inbound** | RDP → TCP 3389 ✅ |

> For initial VM creation, do not manually open additional ports. Only RDP is required at this stage.


---

### Step 12 - Disks

| Setting | Value |
|---------|-------|
| **Disk Configuration** | Default settings ✅ |

> Keep the default disk configuration. No changes required.

---

### Step 13 - Management

| Setting | Value |
|---------|-------|
| **Management Settings** | Default settings ✅ |

> Keep the default management settings. No changes required.

---

### Step 14 — Review + Create

Review the full configuration summary and deploy:

```
Review + Create → Create ✅
```







































<img width="1920" height="1080" alt="Screenshot (560)" src="https://github.com/user-attachments/assets/3a9039a2-2900-4997-9551-e04f83a0d4ea" />


---








































## ✅ Verification

After deployment completes verify the following:

| Check | Expected Result |
|-------|----------------|
| VM Status | Running ✅ |
| Region | Germany West Central ✅ |
| Image | Windows Server 2025 Datacenter ✅ |
| Size | Standard DC1s_v3 ✅ |
| RDP Port 3389 | Open ✅ |
| Public IP | Assigned ✅ |











































































































<img width="1920" height="1080" alt="Screenshot (564)" src="https://github.com/user-attachments/assets/0c6566e5-cf16-4f46-8ceb-3124f3eb914f" />

























































































## 💡 Next Step

→ [RDP into Server](./rdp-into-server.md)
