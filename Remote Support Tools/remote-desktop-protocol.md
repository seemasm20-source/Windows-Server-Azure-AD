
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

2.Open the target Windows VM and obtain its IP address.

3.Press Win + R, type mstsc, and press Enter.

4.Enter the target VM's IP address or hostname.((__sam@seemaenterprise.co.in__)

5.Select Connect and enter the appropriate credentials.

6.Verify that the remote Windows desktop opens successfully.



## Troubleshooting Scenarios

* **Connection timed out:** Check network connectivity, routing, firewall rules and Azure Network Security Group (NSG) rules.

* **Remote Desktop unavailable:** Verify that RDP is enabled and the Remote Desktop Services configuration is working.

* **Authentication failure:** Check the username, password, account status and remote sign-in permissions.

* **Access denied:** Verify that the account is authorised to sign in through Remote Desktop.



## Verification

* Successfully connected to the target Windows VM.

* Confirmed that the remote desktop was accessible.

* Documented any connection issue, its cause the corrective action and the test result.















<img width="1920" height="1080" alt="Screenshot (672)" src="https://github.com/user-attachments/assets/c9cb92e9-b0ff-4562-adea-948b02c57bab" />














































<img width="1920" height="1080" alt="Screenshot (678)" src="https://github.com/user-attachments/assets/7e3f2454-098e-48ff-be9d-875d3ee7181b" />






































<img width="1920" height="1080" alt="Screenshot (674)" src="https://github.com/user-attachments/assets/0d03ee4c-417a-4742-969b-b971f1173f3c" />



















































