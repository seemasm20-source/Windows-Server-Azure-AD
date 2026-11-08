

# 🖥️ Create Windows Server VM on Azure

[ Back to Section 01 README]  → [[Windows Server & Azure AD – GitHub README](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/README.md))

---

## 📋 Summary

Deploy a Windows Server 2025 virtual machine on Microsoft Azure to serve as the Domain Controller for the lab environment.

This is the first step in building an Azure-based Windows Server and Active Directory home lab for practising IT Help Desk Tier 1 and Tier 2 troubleshooting scenarios.

---

## 🔎 Steps to Document

### Step 1 - Create an Azure Account

Create an Azure account and access the Azure Portal:

🔗 [Microsoft Azure Portal](https://portal.azure.com)

---

### Step 2 - Create a Virtual Machine

In the Azure Portal, navigate to:

```text
Virtual Machines → Create → Azure Virtual Machine
```

---

### Step 3 - Resource Group

| Setting | Value |
|---------|-------|
| **Resource Group** | Seema |

Create a new resource group or select an existing one to organize the Azure resources used in this lab.

---

### Step 4 - Virtual Machine Name

| Setting | Value |
|---------|-------|
| **Virtual Machine Name** | server2021 |

---

### Step 5 - Region

| Setting | Value |
|---------|-------|
| **Region** | Germany West Central |
| **Virtual Network Region** | Germany West Central |

> **Note:** The virtual network and the VM's network interface must be in the same Azure region. In this lab, both are deployed in Germany West Central.

---

### Step 6 - Image

| Setting | Value |
|---------|-------|
| **Image** | Windows Server 2025 Datacenter - x64 Gen2 |

---

### Step 7 - VM Size

| Setting | Value |
|---------|-------|
| **VM Size** | Standard DC1s_v3 |
| **vCPU** | 1 |
| **RAM** | 8 GiB |

---

### Step 8 - Administrator Account

Create a local administrator username and password for the Windows Server VM.

```text
Username: [your-admin-username]
Password: [your-strong-password]
```

> **Important:** Store your credentials securely. You will need these credentials to connect to the server using Remote Desktop Protocol (RDP).

---

### Step 9 - Inbound Ports

| Setting | Value |
|---------|-------|
| **Allow Inbound Port** | RDP - TCP 3389 |
| **Source** | My IP / Trusted IP address |

RDP allows remote administration of the Windows Server VM.

> **Security Note:** Restrict RDP access to a trusted source IP address. Avoid exposing TCP port 3389 to the entire internet. For production environments, consider using Azure Bastion or VPN-based access.

---

### Step 10 - Networking

| Setting | Value |
|---------|-------|
| **Virtual Network (VNet)** | vnet-germany-west-central19 |
| **Subnet** | Existing subnet |
| **Region** | Germany West Central |

> **Note:** Ensure that the virtual network and the VM's network interface are deployed in the same region.

---

### Step 11 - Network Interface / Network Security Group (NSG)

| Setting | Value |
|---------|-------|
| **Additional Inbound Ports** | None |
| **Allowed Inbound Traffic** | RDP - TCP 3389 |
| **Source** | Trusted IP address |

The Network Security Group (NSG) controls inbound and outbound network traffic to the virtual machine.

> **Note:** Only the required RDP access is configured at this stage. Additional ports will be opened later only when required for specific lab scenarios.

---

### Step 12 - Disks

| Setting | Value |
|---------|-------|
| **Disk Configuration** | Default settings |

Keep the default disk configuration for this lab.

---

### Step 13 - Management

| Setting | Value |
|---------|-------|
| **Management Settings** | Default settings |

Keep the default management settings for the initial deployment.

---

### Step 14 - Review and Create

Review the complete configuration before deploying the virtual machine.

```text
Review + Create → Create
```

Wait for the deployment to complete successfully.

### 📸 Azure VM Deployment

![Azure Windows Server VM deployment configuration](https://github.com/user-attachments/assets/3a9039a2-2900-4997-9551-e04f83a0d4ea)

---

## ✅ Verification

After deployment completes, verify the following configuration in the Azure Portal.

| Check | Expected Result |
|-------|----------------|
| VM Status | Running |
| Region | Germany West Central |
| Operating System | Windows Server 2025 Datacenter |
| VM Size | Standard DC1s_v3 |
| Virtual Network | Assigned |
| Public IP | Assigned |
| NSG Rule | TCP 3389 allowed from trusted IP |
| Network Interface | Successfully attached |

> **Verification Note:** The NSG rule confirms that RDP traffic is permitted by the network security configuration. Actual RDP connectivity will be tested in the next lab.

### 📸 Successfully Deployed Windows Server VM

![Windows Server 2025 VM overview in Azure Portal](https://github.com/user-attachments/assets/0c6566e5-cf16-4f46-8ceb-3124f3eb914f)

---

## 💡 Key Learnings

- Created and configured a Windows Server 2025 virtual machine using Microsoft Azure.
- Learned how Azure Resource Groups organize cloud resources.
- Understood the relationship between Azure virtual machines, virtual networks, subnets and network interfaces.
- Configured inbound RDP access through a Network Security Group.
- Learned the importance of restricting remote access to trusted IP addresses.

---

## ⚠️ Important - Azure VM Billing

Shutting down Windows from inside the virtual machine does not necessarily stop compute charges.

To stop compute billing when the VM is not needed:

```text
Azure Portal → Virtual Machines → server2021 → Stop
```

Ensure the VM status changes to **Stopped (deallocated)**.

> Storage and other associated resources may continue to incur charges even after the VM is deallocated.

---

## 💡 Next Step

The Windows Server 2025 virtual machine has been successfully deployed.

The next step is to connect to the server remotely using Remote Desktop Protocol (RDP).

→ [RDP into Server](./rdp-into-server.md)






























