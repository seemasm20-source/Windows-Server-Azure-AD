# 💻 Create Windows 11 Client VM on Azure

[← Back to Section 01 Overview](./README.md)

---

## 📋 Summary

Set up a Windows 11 Pro virtual machine on Microsoft Azure to act as the client machine for the lab environment. This client VM will be joined to the domain and used to test Active Directory, Group Policy, VPN and remote support scenarios.

---

## 🔎 Steps to Document

### Step 1 — Resource Group

| Setting | Value |
|---------|-------|
| **Resource Group** | Seema ✅ |

> Use the same resource group as the server VM so both machines are managed together.


---

### Step 2 — Select Virtual Machine Type

In the Azure Portal:

```
Virtual Machines → Create → Azure Virtual Machine
```

| Setting | Value |
|---------|-------|
| **Machine Type** | Windows 11 ✅ |


---

### Step 3 — Region

| Setting | Value |
|---------|-------|
| **Region** | Germany West Central ✅ |

> **Note:** Must be the same region as the server VM (server2021) so both machines are on the same Virtual Network.


---

### Step 4 — Image

| Setting | Value |
|---------|-------|
| **Image** | Windows 11 Pro version 25H2 — x64 Gen2 ✅ |


---

### Step 5 — VM Size

| Setting | Value |
|---------|-------|
| **VM Size** | Standard DC1s_v3 ✅ | | **vCPU** | 1 | | **RAM** | 8 GiB |



---

### Step 6 — Administrator Account

Create a local administrator username and password for the client VM.

```
Username: [your-admin-username]
Password: [strong-password — write this down securely]
```

> **Note:** You can use the same credentials as the server VM for simplicity in a lab environment.

---

### Step 7 — Inbound Ports

| Setting | Value |
|---------|-------|
| **Allow inbound port** | RDP — TCP 3389 ✅ |

> This allows remote administration of the Windows 11 client via Remote Desktop Protocol.


---

### Step 8 — Networking

| Setting | Value |
|---------|-------|
| **Virtual Network (VNet)** | vnet-germany-west-central1 ✅ |
| **Subnet** | Same subnet as server VM ✅ |
| **Region** | Germany West Central ✅ |

> **Important:** The Virtual Network and Subnet must be in the same location - Germany West Central. This ensures the client VM and server VM can communicate with each other on the same network.



---

### Step 9 - Remaining Settings

| Setting | Value |
|---------|-------|
| **Disks** | Default settings ✅ |
| **Management** | Default settings ✅ |
| **Monitoring** | Default settings ✅ |
| **Advanced** | Default settings ✅ |

> Keep all remaining settings at default. No changes required.

---

### Step 10 — Review + Create

Review the full configuration summary and deploy:

```
Review + Create → Create ✅
```
















<img width="1920" height="1080" alt="Screenshot (565)" src="https://github.com/user-attachments/assets/a309d5db-d9c5-46a7-b730-ac229d8d0da4" />
























---

## ✅ Verification

After deployment completes verify the following:

| Check | Expected Result |
|-------|----------------|
| VM Status | Running ✅ |
| Region | Germany West Central ✅ |
| Image | Windows 11 Pro version 25H2 ✅ |
| Size | Standard DC1s_v3 ✅ |
| RDP Port 3389 | Open ✅ |
| Public IP | Assigned ✅ |
| VNet | vnet-germany-west-central1 ✅ |






<img width="1920" height="1080" alt="Screenshot (568)" src="https://github.com/user-attachments/assets/6d5756c8-fd77-47d6-b482-5303f1a626b7" />


---

## 📋 Client VM Configuration Summary

| Setting | Value |
|---------|-------|
| **Resource Group** | Seema |
| **VM Type** | Windows 11 |
| **Region** | Germany West Central |
| **Image** | Windows 11 Pro version 25H2 — x64 Gen2 |
| **VM Size** | Standard DC1s_v3 |
| **vCPU** | 1 |
| **RAM** | 8 GiB |
| **Inbound Port** | RDP TCP 3389 |
| **VNet** | vnet-germany-west-central1 |
| **Remaining settings** | Default |

---



---

## 💡 Next Step

→ [RDP into Server](./rdp-into-server.md)
