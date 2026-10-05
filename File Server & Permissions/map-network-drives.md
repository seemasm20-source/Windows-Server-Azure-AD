

## 🖥️ Map Network Drives Manually




## Method 1 (GUI) : Configuration on the Windows Server (Host Machine)

 ## Step 1 : Before a client can connect, you must create and share a target folder.

1. Create the Folder: Open File Explorer, navigate to where you want the shared folder to live (e.g. C:\),

   right-click, and select New > Folder. Name it (e.g., Companyshare).
   
2. Open Sharing Properties: Right-click your new folder and select Properties. Go to the Sharing tab.
   
3. Configure Advanced Sharing:
   
	 • Click Advanced Sharing.

	 • Check the box for Share this folder.

	 • Click Permissions to define who can access it. (Selected user __SAM__ assigning him Read & Change access). Click OK, then Apply.

5.  Copy the Network Path: Back on the main Sharing tab, look at the Network Path field. It will look like __\\server2021\Companyshare__ Copy or write this path down; you will         need it on the client machine.



## Step 2: Mapping the Drive on the Client Machine Using File Explorer (GUI)



1. Open File Explorer (Windows Key + E).

2. Click on This PC in the left sidebar.
3. Find the Map Network Drive tool
	• Windows 11: Click the three dots (...) icon in the top toolbar and select Map network drive.


5.  In the setup window.

	• Drive: Choose an available drive letter (e.g., Z:) from the dropdown.

	• Folder: Paste or type the server network path you copied in Step 1 (\\server2021\Companyshare).

	• Check Reconnect at sign-in so the drive persists after a computer reboot.

	• Check Connect using different credentials if your client login differs from your server/Active Directory account.

    •  Click Finish. 




<img width="1920" height="1080" alt="Screenshot (622)" src="https://github.com/user-attachments/assets/d3a1555f-5293-4c54-9eb8-f755c33ff851" />

















































<img width="1920" height="1080" alt="Screenshot (623)" src="https://github.com/user-attachments/assets/9e4f2813-220e-45a1-85d6-3abd5aa5dcef" />

















































<img width="1920" height="1080" alt="Screenshot (624)" src="https://github.com/user-attachments/assets/b69fde9d-f79e-4988-a665-480787ea92b1" />












































<img width="2160" height="2371" alt="1C8DF743-B541-4A0B-B2B6-8BF0B21B94F2" src="https://github.com/user-attachments/assets/cbf5e807-9220-4855-99dd-6d19495506d7" />































<img width="2160" height="2766" alt="18CACAA1-D3F3-455E-A1DE-E4FE83F69DFB" src="https://github.com/user-attachments/assets/025ea7bf-11bc-42d3-8957-874ab686f6eb" />














































<img width="2160" height="2766" alt="D3803D7B-4D5C-471A-A44A-8F581B512EAF" src="https://github.com/user-attachments/assets/ca8a56d4-bf5f-4811-80d7-fe87b7c42d8a" />



