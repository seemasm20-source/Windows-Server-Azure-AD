# 🖥️ Remote Desktop Protocol (RDP)

[ Back to Overview] → [Remote Support Tools – Overview](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Remote%20Support%20Tools/remote-support-tools-overview.md)

---

## 📋 Summary

Connect to the Windows 11 client VM and the Windows Server VM in Azure with Remote Desktop Connection (`mstsc`). RDP is how IT support reaches a remote Windows computer and works on it as if sitting in front of it.

---

## 💡 What is RDP?

Remote Desktop Protocol (RDP) is a Microsoft protocol that lets an authorised user connect to a remote Windows computer and use its graphical desktop.

| Setting | Value |
|---------|-------|
| **Platform** | Microsoft Azure |
| **Remote machines** | Windows 11 Pro client VM and Windows Server VM (`server2021`) |
| **Tool** | Remote Desktop Connection (`mstsc`) |
| **Protocol and port** | RDP, TCP 3389 |
| **Account used** | `sam@seemaenterprise.co.in` |

> A computer can only be the **target** of an RDP connection if it runs Windows Pro, Enterprise or Server. Windows Home can start a connection but cannot receive one.

---

## 🔧 Steps

### Step 1 - Get the Address of the Target VM

1. Sign in to the **Azure portal**.
2. Open the target VM. On the **Overview** page, copy its IP address:

| Connecting from | Address to use |
|-----------------|----------------|
| Outside Azure, such as your own PC | The VM's **public IP address**. This needs an inbound rule for TCP 3389 on the VM's network security group (NSG) |
| Inside the same virtual network, such as from the Domain Controller | The VM's **private IP address** or its hostname |

### Step 2 - Allow the User to Connect (on the Windows 11 Client)

A standard domain user can connect with Remote Desktop only if they are a member of the **Remote Desktop Users** group on the target computer. On the Windows 11 client:

1. Open **Settings → System → Remote Desktop**.
2. Select **Remote Desktop users**.
3. Click **Add...**, type `Sam`, click **Check Names**, then **OK**.

`Sam` is now listed as a Remote Desktop user.

> Administrators can connect without this step. Without it, a standard user such as Sam is denied.


### Step 3 - Open Remote Desktop Connection

1. Press **Win + R**, type `mstsc` and press **Enter**.
2. In the **Computer** box, enter the target VM's IP address or hostname.
3. Click **Show Options** if you want to enter the username in advance.

**Screenshot: Remote Desktop Connection window:**

<img width="1920" height="1080" alt="Remote Desktop Connection window with the target VM address entered" src="https://github.com/user-attachments/assets/c9cb92e9-b0ff-4562-adea-948b02c57bab" />

**Screenshot: sign-in prompt:**

<img width="1920" height="1080" alt="Windows Security prompt asking for the credentials of the remote VM" src="https://github.com/user-attachments/assets/0d03ee4c-417a-4742-969b-b971f1173f3c" />


### Step 4 - Connect and Sign In

1. Click **Connect**.
2. Enter the credentials for the target:

```text
Username: SEEMAENTERPRISE\Sam      (or sam@seemaenterprise.co.in)
Password: <password>
```


3. If a certificate warning appears, it is normal in a lab, because the VM uses a self-signed certificate. Click **Yes** to continue.



**Screenshot: remote desktop session:**

<img width="1920" height="1080" alt="Remote desktop session open on the target Windows VM" src="https://github.com/user-attachments/assets/7e3f2454-098e-48ff-be9d-875d3ee7181b" />

---



### Step 5 - Confirm the Remote Desktop Opens

The remote Windows desktop opens in a window, with a connection bar at the top.


---

## 🛠️ Troubleshooting RDP

| Symptom | Likely cause | What to check |
|---------|--------------|---------------|
| **Remote Desktop can't connect to the remote computer** (connection times out) | The VM is stopped, the address is wrong, or TCP 3389 is blocked | VM status in Azure, the IP address, the NSG inbound rule for 3389, and the Windows firewall. Test the port with `Test-NetConnection <IP> -Port 3389` |
| **Remote Desktop can't find the computer** | The hostname does not resolve | Use the IP address instead, then check DNS |
| **Your credentials did not work** | Wrong username, password or domain format | Use `SEEMAENTERPRISE\Sam` or the full `@seemaenterprise.co.in` name, and check that the account is enabled and not locked |
| **The connection was denied because the user account is not authorized for remote login** | The user is not allowed to connect | Add the user in **Settings → System → Remote Desktop → Remote Desktop users**, or add them to the **Remote Desktop Users** group |
| **Remote Desktop is not available on the target** | Remote Desktop is off, or the edition is Windows Home | Turn on **Remote Desktop** in Settings and check the Windows edition |





---

## 💡 Next Step

→ [Remote Computer Management](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/Remote%20Support%20Tools/remote-computer-mgt.md)









