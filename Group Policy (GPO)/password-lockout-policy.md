
## 🖥️Password and Lockout Policy


## Step 1: Locate the Default Domain Policy

1.  Open Group Policy Management (gpmc.msc).
      
2. Expand your Forest -> Domains -> and click on your root domain name __(seemaenterprise.co.in)__
 
3. You will see a policy named Default Domain Policy linked here.
 
4. Right-click Default Domain Policy and select Edit. (This opens the Group Policy Management Editor).


## Step 2: Configure Password Complexity & Length

1. In the left pane of the editor, navigate down through the Computer Configuration branch
   
	 • Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Password Policy

2. In the right pane, double-click and configure these core settings based on your security requirements:
   
	 • Minimum password length: Set this to at least 12 or 14 characters (modern security standard).

	 • Password must meet complexity requirements: Set to Enabled (forces a mix of uppercase, lowercase, numbers, and symbols).

	 • Maximum password age: Set to 0 (never expires, recommended if using long passphrases) or 90 days (traditional compliance standard).

	 • Enforce password history: Set to 24 passwords remembered (prevents users from reusing old passwords immediately).


## Step 3: Configure Account Lockout (Brute-Force Protection)

1. In the left pane, click on the folder directly below Password Policy named Account Lockout Policy.
   
2. Double-click and configure these three interdependent settings:
   
	 • Account lockout threshold: Set this to 5 invalid logon attempts (the account locks after 5 wrong passwords).

     Note: When you hit Apply, Windows will pop up a box suggesting default times for the next two settings. Click OK, or manually change them below

	 • Account lockout duration: Set to 30 minutes (how long the user has to wait before the account unlocks itself).

	 • Reset account lockout counter after: Set to 30 minutes (how long Windows waits between clean logins before wiping the "failed attempt history" back to zero).



## Step 4: Force and Test the Policy

 1. Close the GPO Editor window.
 
 2. Because this is a Computer Configuration policy, client computers must download it during startup or background refreshes.
  
 3. On a client machine, open Command Prompt as Administrator and type

   gpupdate /force
   
 4. The Test: To confirm it took effect, log out of a client machine and purposefully type a wrong password 5 times in a row.

   It should block you and state that the account has been locked. You can unlock the user manually in Active Directory user properties.

   







