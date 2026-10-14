
# Remote Event Viewer

Remote Event Viewer allows IT support technicians to inspect event logs on another Windows computer without starting a full Remote Desktop session. It helps investigate application crashes, unexpected shutdowns, system errors and authentication issues.

## Environment

* **Platform:** Microsoft Azure
* **Admin machine:** Windows Client VM or Windows Server VM
* **Target machine:** Remote Windows computer
* **Tool:** Event Viewer (`eventvwr.msc`)
* **Log type:** Windows Logs -System, Application and Security



## Steps to Connect

1. Sign in to the Windows machine you will use for administration.
2. Press `Win + R`, type `eventvwr.msc`, and press Enter.
3. In the Event Viewer console, right-click **Event Viewer (Local)**.
4. Select **Connect to Another Computer**.
5. Select **Another computer** and enter the target computer's hostname, such as `server2021`, or its IP address.
6. Click **OK** and wait for the remote logs to load.
7. Expand **Windows Logs**.
8. Select **System** or **Application** to inspect the target computer's events.
9. Open an event and review its source, Event ID, timestamp, general description and details.

## Common Troubleshooting Examples

* **System errors:** Review the System log for unexpected shutdowns, driver problems or service failures.
* **Application crashes:** Review the Application log for application errors.
* **Failed logons:** Review the Security log when the required audit events are available and your account has permission to read them.
* **Cannot connect:** Check the target hostname, DNS resolution, network connectivity, firewall configuration and remote Event Log access.
* **Access denied:** Verify that the account has the required permissions on the target computer.

## Verification

* Confirm whether the remote computer's logs load successfully.
* Open a relevant event and inspect its details.
* If a connection issue occurs, record the error and troubleshoot it.
* Document the cause, corrective action and retest result only if you actually identified and tested a fix.




<img width="2147" height="1994" alt="FDF57365-ACCF-4C27-828C-CF2E72B8EA33" src="https://github.com/user-attachments/assets/80495adf-9f59-4bb6-a652-228ec5bcee39" />

