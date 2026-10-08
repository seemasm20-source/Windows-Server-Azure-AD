

## 🖥️Restrict Control Panel Access


## Step 1: Create a Dedicated GPO

1. On your Domain Controller, open Group Policy Management (gpmc.msc).
2. Go to the Group Policy Objects folder, right-click it, and select New.
3. Name it GPO_Restrict_Control_Panel and click OK.
4. Right-click the new GPO and select Edit




## Step 2: Choose Your Level of Restriction

Inside the Group Policy Management Editor, navigate down through the user branch:

• User Configuration > Policies > Administrative Templates > Control Panel

In the right pane, you have two options depending on how strict you want to be:

Option A: Total Lockdown (Block Everything)

This completely bans the user from opening the Control Panel or the Windows Settings app.

1. Double-click Prohibit access to Control Panel and PC settings.
2. 
3. Change the setting to Enabled.
4. Click Apply and then OK.






## Step 3: Link the GPO to Your Target OU

1. Close the GPO Editor window.
2. In the main console, find the OU containing the User Accounts you want to restrict (e.g., your Sales, HR, or Standard Users OU).
	• ⚠️ Note: Do not link this to your IT OU, or you will lock yourself out of the Control Panel on client machines!
3. Right-click the OU and select Link an Existing GPO...
4. Select GPO_Restrict_Control_Panel and click OK.




## Step 4: Test it on the Client Machine

1. Go to your Windows client machine and log in as a user who sits inside that restricted OU (e.g., Sam, if his account is in that OU).
2. Open Command Prompt and refresh the policy:gpupdate /force



1. The Test: Try to open the Control Panel or right-click the desktop and select Display settings.
If you chose Option A (Total Lockdown), Windows will instantly block the request and display an explicit error message:

This operation has been cancelled due to restrictions in effect on this computer. Please contact your system administrator."

   
