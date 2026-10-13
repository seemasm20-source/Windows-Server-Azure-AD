
# Remote Computer Management





Remote Computer Management allows an IT support technician to administer another Windows computer without opening a full remote desktop session. Depending on permissions and configuration, it can be used to manage services, view Event Viewer logs, access shared folders and perform other administrative tasks.



## Environment

* **Platform:** Microsoft Azure
* **Admin machine:** Windows computer used to connect remotely
* **Target machine:** Windows Client VM or Windows Server VM
* **Tool:** Computer Management (`compmgmt.msc`)



## Procedure

1. Sign in to the Windows machine you will use for administration.
2. Press `Win + R`, type `compmgmt.msc`, and press Enter.
3. In the Computer Management console, right-click **Computer Management (Local)**.
4. Select **Connect to another computer**.
5. Enter the target computer's hostname, such as `server2021`, or its IP address.
6. Click **OK** and wait for the remote computer's management console to load.
7. Expand the available management sections and check which tools you can access.

## Troubleshooting Scenarios

* **Cannot connect to the remote computer:** Verify the hostname or IP address, network connectivity, and firewall configuration.
* **Access denied:** Check whether the account has the required administrative permissions on the target computer.
* **Remote management unavailable:** Check the relevant Windows services, firewall rules, and remote management configuration.
* **Hostname not resolving:** Verify DNS configuration or test the connection using the target computer's IP address.

## Verification

* Confirm whether the remote computer connects successfully.
* Check which management sections are accessible.
* If a connection fails, record the error message and investigate the cause.
* Document the corrective action and retest the connection, if troubleshooting was performed.























<img width="1920" height="1080" alt="Screenshot (680)" src="https://github.com/user-attachments/assets/b7c44da7-afad-4b50-9c34-b0f4240b2b75" />



































<img width="1920" height="1080" alt="Screenshot (681)" src="https://github.com/user-attachments/assets/d3a66ad7-155b-40b1-b088-ad025741bf06" />













































<img width="1920" height="1080" alt="Screenshot (682)" src="https://github.com/user-attachments/assets/27ccba73-670a-4b40-9ec8-e37cbfbf8a7c" />





















































<img width="1920" height="1080" alt="Screenshot (685)" src="https://github.com/user-attachments/assets/35fedf20-d734-40e6-85dd-c79c7840fbcc" />



























































<img width="1920" height="1080" alt="Screenshot (683)" src="https://github.com/user-attachments/assets/b8bbd93d-5cf9-4618-ada5-6af7cfe8bd84" />





