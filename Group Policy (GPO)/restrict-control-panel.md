

## 🖥️Restrict Control Panel Access

 
## Step 1: Create a Dedicated GPO

1. On your Domain Controller, open Group Policy Management (gpmc.msc).
   
2. Go to the Group Policy Objects folder, right-click it, and select New.
 
3. Name it __GPO_Restrict_Control_Panel__ and click OK.
   
4. Right-click the new GPO and select Edit




## Step 2: Choose Your Level of Restriction

Inside the Group Policy Management Editor, navigate down through the user branch:

• User Configuration > Policies > Administrative Templates > Control Panel

In the right pane, you have two options depending on how strict you want to be

## Option A: Total Lockdown (Block Everything)

This completely bans the user from opening the Control Panel or the Windows Settings app.

1. Double-click Prohibit access to Control Panel and PC settings.
   
2. Change the setting to Enabled.
   
3. Click Apply and then OK.




## Option B: Partial Access (Hide/Show Specific Applets)

  If you want to let users access basic settings (like Printers) but hide dangerous ones (like Programs and Features and Network Connections)

1. Double-click Hide specified Control Panel items.

2. Change it to Enabled, then click the Show... button.
   
3. Type the exact canonical name of the item you want to hide (e.g., Microsoft.NetworkAndSharingCenter or   Microsoft.ProgramsAndFeatures).
   
4. Click OK, then Apply


## Step 3: Link the GPO to Your Target OU

1. Close the GPO Editor window.
   
2. In the main console, find the OU containing the User Accounts you want to restrict
	
3. Right-click the IT OU and select Link an Existing GPO...
   
4. Select GPO_Restrict_Control_Panel and click OK.




## Step 4: Test it on the Client Machine

1. Go to your Windows client machine and log in as a user __SAM__ who sits inside that restricted IT OU 

2. Open Command Prompt and refresh the policy: gpupdate /force



 1. The Test: Try to open the Control Panel or right-click the desktop and select Display settings.
   
   __Option A__: (Total Lockdown), Windows will instantly block the request and display an explicit __error message__:

   __This operation has been cancelled due to restrictions in effect on this computer. Please contact your system administrator.__

 __OPTION B__: Partial Access (Hide/Show Specific Applets)

   Hides Program&Features AND Network&Sharing Center. 

   Note: I have tested both option A and Option B.














   <img width="1920" height="1080" alt="Screenshot (653)" src="https://github.com/user-attachments/assets/153dacd9-faa2-4e99-b2aa-b3ee6833c587" />





































<img width="1920" height="1080" alt="Screenshot (654)" src="https://github.com/user-attachments/assets/8ee91199-a677-4a03-bd8b-a3bfb443ea76" />



























































<img width="1920" height="1080" alt="Screenshot (656)" src="https://github.com/user-attachments/assets/a8996561-ef5a-4001-befd-a3e26713f800" />

















<img width="1920" height="1080" alt="Screenshot (655)" src="https://github.com/user-attachments/assets/f6a7b9c2-b75b-4cef-ac60-d28086a60b58" />



















<img width="1920" height="1080" alt="Screenshot (657)" src="https://github.com/user-attachments/assets/5a1c1fd4-1d99-4c08-af9a-b1f66143d18f" />
































<img width="2268" height="3119" alt="IMG_0517" src="https://github.com/user-attachments/assets/79c3e409-193b-476a-9e71-d47eafab5995" />










































<img width="1920" height="1080" alt="Screenshot (658)" src="https://github.com/user-attachments/assets/a1aad35a-c67d-4bb5-ab63-5949d65b2a40" />

















































<img width="1920" height="1080" alt="Screenshot (659)" src="https://github.com/user-attachments/assets/334f68f0-3411-486d-8ae1-b4f45d40f4b0" />




























































<img width="2268" height="2206" alt="IMG_0522" src="https://github.com/user-attachments/assets/aed2e2f0-05b4-4c0b-813c-d1efd29449f7" />





























<img width="2185" height="2514" alt="IMG_0524" src="https://github.com/user-attachments/assets/f604b69a-5c58-46e1-98e3-b2df219ef0f7" />
