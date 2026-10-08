
# 🖥️ Event Viewer

**Event Viewer** is a built-in Windows administrative tool used to **view, monitor and troubleshoot system, security, application and service events**.

Windows records important activities and errors as **event logs**. IT administrators and support technicians can use Event Viewer to identify problems, investigate errors and understand what happened on a Windows computer or server.

## Common Event Logs

- **Application** – Records events related to applications and software.
- **System** – Records Windows system, driver and service events.
- **Security** – Records security-related activities such as logons, account changes and account lockouts.
- **Setup** – Records Windows installation and setup events.
- **Forwarded Events** – Stores events collected from other computers.

## Important Event Information

Each event can contain:

- **Event ID** – Identifies the specific event.
- **Level** – Information, Warning, Error or Critical.
- **Source** – The Windows component or service that generated the event.
- **Date and Time** – When the event occurred.
- **Description** – Details about what happened.

## Example

For an Active Directory environment:

**Event ID 4740 – A user account was locked out**

An IT support technician can use Event Viewer on the **Domain Controller → Windows Logs → Security** to investigate account lockout events.

## How to Open Event Viewer

Press:

`Win + R` → type `eventvwr.msc` → **Enter**

## IT Support Use

Event Viewer is commonly used to troubleshoot:

- Windows errors and crashes
- Application failures
- Login and authentication problems
- Account lockouts
- Service failures
- Driver issues
- Security-related events
- System startup and shutdown problems
