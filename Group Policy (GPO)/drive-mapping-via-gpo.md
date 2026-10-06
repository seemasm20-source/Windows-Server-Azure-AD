
## Drive Mapping via GPO

## Step:1 Setting Up the Drive Map


1. Navigate to Drive Maps:
	• In the left pane of the editor window, double-click User Configuration.
	• Double-click Preferences.
	• Double-click Windows Settings.
	• Click on Drive Maps.
2. Create the New Mapped Drive:
	• Right-click anywhere in the empty white space on the right-hand pane, or right-click Drive Maps on the left.
	• Select New > Mapped Drive.
3. Configure the Drive Properties:
	• Action: Select Update from the dropdown menu.
	• Location: Type your full network path (e.g., \\SERVER2021\Companyshare).
	• Drive Letter: Near the bottom, check Use: and select your desired letter (like G).
	• Click





## Step 2: Confirm the GPO Link is Active
Because you created the GPO by right-clicking a specific OU, it should already be linked. Let's make sure it is turned on.
1. Close the Group Policy Management Editor window so you are back in the main Group Policy Management Console (GPMC).
2. Click on the OU where you originally created the policy ( IT OU).
3. Look under that OU in the left tree. You should see your GPO name ( HR-Restriction )
4. Click on the GPO name under that OU and look at the right pane:
	• Go to the Scope tab. Under Links, ensure your OU is listed and Link Enabled says Yes.
	• Under Security Filtering, it should say Authenticated Users. This ensures anyone inside that OU gets the drive.


## Step 3: Force the Policy onto the Client Machine

1. Go to the Windows client computer and log in as a user who belongs to that target OU.
2. Open the Command Prompt 
3. Type the following command and press ENTER
    gpupdate /force

4.  Wait for it to complete. It should say:
	• "Computer Policy update has completed successfully."
	• "User Policy update has completed successfully."


## Step 4 : Verify the Drive Map 

Now you need to verify that the policy actually executed on the client machine.

1. Check File Explorer: Open File Explorer and click on This PC. Look under Network locations. Do you see your mapped drive(:G) letter sitting there
                                              OR
2. Check via Command Line: If you don't see it visually, open Command Prompt on the client and type:

 net use

 Press Enter. Look to see if your drive letter and server path are listed in the table with a status of OK.



































 
