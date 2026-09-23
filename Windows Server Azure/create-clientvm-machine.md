




# 🖥️ Create Windows Server VM on Azure


---

## 📋 Summary

Set up a Windows Client 2025 virtual machine on Microsoft Azure to act as the Domain Controller for the lab environment.

---

## 🔎 Steps to Document


---

### Step 1 - Create a Virtual Machine

In the Azure Portal:

```
Virtual Machines → Create → Azure Virtual Machine
```


---

### Step 2 - Resource Group

| Setting | Value |
|---------|-------|
| **Resource Group** | Seema ✅ |


---

### Step 4 - Virtual Machine Name

| Setting | Value |
|---------|-------|
| **Virtual Machine Name** | Windows11  |

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
| **Image** | Windows 11 Pro version 25H2 x64 -Gen2 ✅ |



---

### Step 7 - VM Size

| Setting | Value |
|---------|-------|
| **VM Size** | Standard DC1s_v3 ✅ | | **vCPU** | 1 | | **RAM** | 8 GiB |


---

### Step 8 - Administrator Account

Create a local server administrator username and password.

```
Username: [your-admin-username]
Password: [strong-password — write this down securely]
```

> **Important:** Store your credentials securely. You will need them every time you RDP into the client machine.

---

### Step 9 - Inbound Ports

| Setting | Value |
|---------|-------|
| **Allow inbound port** | RDP - TCP 3389 ✅ |

> This allows remote administration of the Windows client  via Remote Desktop Protocol.


---

### Step 10 - Networking

| Setting | Value |
|---------|-------|
| **Virtual Network (VNet)** | vnet-germany-west-central19 |
| **Subnet** | Existing subnet |
| **Region** | Germany West Central ✅ |

> **Note:** Ensure the VNet and the VM are both located in Germany West Central just like the server


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




<img width="1920" height="1080" alt="Screenshot (565)" src="https://github.com/user-attachments/assets/f72c6321-7b9c-43c2-91db-b1b59d4e7105" />















































<img width="1920" height="1080" alt="Screenshot (568)" src="https://github.com/user-attachments/assets/2212d8cb-347f-4c43-a951-74bd4cecf928" />

