
# Remote Desktop Protocol (RDP)

Remote Desktop Protocol (RDP) is a Microsoft protocol that allows an authorised user to connect to and interact with a remote Windows computer through a graphical desktop session.

## Environment

* **Platform:** Microsoft Azure
* **Remote machines:** Windows Client VM and Windows Server VM
* **Tool:** Remote Desktop Connection (`mstsc`)
* **Protocol:** RDP
* **Default port:** TCP 3389



## Steps to connect

1. Sign in to the Azure portal.

2. Open the target Windows VM and obtain its IP address.

3. Press `Win + R`, type `mstsc`, and press Enter.

4. Enter the target VM's IP address or hostname.

5. Select **Connect** and enter the appropriate credentials.

6. Verify that the remote Windows desktop opens successfully.

## Troubleshooting Scenarios

* **Connection timed out:** Check network connectivity, routing, firewall rules and Azure Network Security Group (NSG) rules.
* **Remote Desktop unavailable:** Verify that RDP is enabled and the Remote Desktop Services configuration is working.
* **Authentication failure:** Check the username, password, account status and remote sign-in permissions.
* **Access denied:** Verify that the account is authorised to sign in through Remote Desktop.

## Verification

* Successfully connected to the target Windows VM.
* Confirmed that the remote desktop was accessible.
* Documented any connection issue, its cause, the corrective action and the test result.

## Security Considerations

* Use strong credentials and authorised accounts.
* Restrict inbound TCP 3389 to trusted IP addresses where possible.
* Avoid exposing RDP directly to the public internet when a safer option, such as Azure Bastion or a VPN, is available.
* Never include passwords, private keys or sensitive connection details in screenshots or documentation.

## Key Learning

Practised remote Windows administration and learned to troubleshoot RDP connectivity, authentication and permission issues in an Azure environment.
