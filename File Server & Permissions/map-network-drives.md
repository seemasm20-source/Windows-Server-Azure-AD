

## 🖥️ Map Network Drives Manually




## Method 1 (GUI) : Configuration on the Windows Server (Host Machine)

 ## Step 1 : Before a client can connect, you must create and share a target folder.

1. Create the Folder: Open File Explorer, navigate to where you want the shared folder to live (e.g., C:\), right-click, and select New > Folder. Name it (e.g., Companyshare).
2. Open Sharing Properties: Right-click your new folder and select Properties. Go to the Sharing tab.
3. Configure Advanced Sharing:
	 • Click Advanced Sharing.
	 • Check the box for Share this folder.
	 • Click Permissions to define who can access it. (Selected user __SAM__ assigning him Read & Change access). Click OK, then Apply.
4.  Copy the Network Path: Back on the main Sharing tab, look at the Network Path field. It will look like __\\server2021\Companyshare__ Copy or write this path down; you will         need it on the client machine.



## Step 2: Mapping the Drive on the Client Machine Using File Explorer (GUI)



1. Open File Explorer (Windows Key + E).
2. Click on This PC in the left sidebar.
3. Find the Map Network Drive tool:
	• Windows 11: Click the three dots (...) icon in the top toolbar and select Map network drive.


4.  In the setup window.
	• Drive: Choose an available drive letter (e.g., Z:) from the dropdown.
	• Folder: Paste or type the server network path you copied in Step 1 (\\server2021\Companyshare).
	• Check Reconnect at sign-in so the drive persists after a computer reboot.
	• Check Connect using different credentials if your client login differs from your server/Active Directory account.
  •  Click Finish. 

























