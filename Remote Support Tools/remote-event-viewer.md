
# Remote Event Viewer Lab

## Objective

Practise viewing and troubleshooting Windows event logs on a remote computer using Event Viewer.

## Environment

* **Platform:** Microsoft Azure
* **Admin machine:** Windows Client VM or Windows Server VM
* **Target machine:** Remote Windows computer
* **Tool:** Event Viewer (`eventvwr.msc`)
* **Log type:** Windows Logs — System, Application and Security

## What Is Remote Event Viewer?

Remote Event Viewer allows IT support technicians to inspect event logs on another Windows computer without starting a full Remote Desktop session. It helps investigate application crashes, unexpected shutdowns, system errors and authentication issues.

## Procedure

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

## Security Considerations

* Access event logs only on computers you are authorised to administer.
* Security logs may contain usernames, computer names and other sensitive information.
* Remove or redact sensitive details from screenshots before publishing them on GitHub.
* Use least-privilege access wherever possible.

## Key Learning

Practised accessing remote Windows event logs and learned how Event Viewer supports IT troubleshooting without requiring a full remote desktop session.

## Evidence to Add

* Screenshot of Event Viewer connected to the remote computer.
* Screenshot showing the remote computer's System or Application log.
* Screenshot of an event's details, with sensitive information redacted.
* Troubleshooting notes, if an issue was encountered.
