
Join Windows 11 Client to Domain

Steps to document: 

1. Connect to the Windows Client :- Log in to the Windows Client VM using Remote Desktop (RDP).








<img width="1920" height="1080" alt="Screenshot (577)" src="https://github.com/user-attachments/assets/6bc1748d-f7f0-4fdf-8ec3-adaa5f8b8451" />







2. Open Network Adapter Settings

Press: Win + R

Type: ncpa.cpl

Press Enter.

The Network Connections window will open.











<img width="2268" height="1724" alt="IMG_0419" src="https://github.com/user-attachments/assets/4e7c6d06-dd58-49e2-8a3d-400c6d0b7391" />









































3. Configure the DNS Server
 
   Right-click the active Network Adapter.
 
 Select Properties →  Select Internet Protocol Version 4 (TCP/IPv4) →  Click Properties 
 
  →  Select: Use the following DNS server addresses

 →   Enter the Domain Controller / DNS Server IP address:

  →  Preferred DNS server: 172.16.0.4














<img width="2268" height="4032" alt="IMG_0421" src="https://github.com/user-attachments/assets/7f844de5-28b9-4cd8-8024-a5730196333e" />





















4. Open System Properties

From the Windows Start menu, search for:

 →  Advanced system settings  → Open View advanced system settings  → The System Properties window will appear.









5. Open Computer Name Settings

In System Properties:

Select the Computer Name tab.
Click Change...









<img width="2268" height="4032" alt="IMG_0422" src="https://github.com/user-attachments/assets/1a9ac40d-40cb-427b-963a-2b73f4d7fbe8" />













6. Join the Domain

Under Member of, select:

Domain

Enter the Active Directory domain name: seemaenterprise.co.in


Click : OK




<img width="2268" height="1985" alt="IMG_0424" src="https://github.com/user-attachments/assets/9c72e839-438b-4157-a1de-e67eb49c73ee" />





























7. Enter Domain Administrator Credentials

Windows will display a Windows Security prompt.

Enter the domain administrator credentials:

Username:

seemaenterprise.co.in\seema

Password:

<Domain Administrator Password>

Click OK.















8. Confirm Domain Join

If the credentials and DNS configuration are correct, Windows should display a message similar to:

Welcome to the seemaenterprise.co.in domain.

Click OK.

Windows may then display a message indicating that the computer needs to be restarted.







9. Restart the Windows Client

Click OK, then restart the Windows Client.

After the restart, the client will be a member of:seemaenterprise.co.in





10. Verification

After restarting, log in and verify the domain membership.

Press: Win + R

Type: sysdm.cpl

Go to the Computer Name tab

Verify that Domain shows: seemaenterprise.co.in










<img width="2268" height="1985" alt="IMG_0424" src="https://github.com/user-attachments/assets/54990c19-1c76-4786-b77f-ce97e944ee72" />
