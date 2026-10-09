

## Event ID 4740 — Account Locked Out    



 Step 1: Trigger the Lockout on the Client Machine

1. Sit down at your Windows 11 client computer.
   
2. If you are logged in, press Windows Key + L to lock the screen.
   
3. Select Sam's account and deliberately type a wrong password.
 
4. Press Enter. Repeat this 5 times in a row (or whatever number you configured in your lockout policy threshold).
 
5. On the 5th or 6th try, the screen must change and explicitly say:"The referenced account is currently locked out and may not be logged on to."



## Step 2: Check the Lockout Event on the Server


1. Log into server2021.
   
2. Press Win + R, type eventvwr.msc, and press Enter to open the Event Viewer.
  
3. In the left sidebar, expand Windows Logs and click on Security.
   
4. Look at the right-hand panel and click Filter Current Log...
   
5. In the box that says <All Event IDs>, type 4740 and click OK.
    
6. The Result: You will see an entry pop up at the exact time you locked the account. Click it, and the description will explicitly read: Target Account Name: Sam and Caller           Computer Name: WINDOWS11.


   
## Step 3: Unlock Sam's Account in ADUC


1. On the server, open Active Directory Users and Computers 

2. Navigate to your IT OU where Sam's user account lives.

3. Right-click Sam and select Properties.

4. Click on the Account tab at the top.

5. Look near the middle of the window. You will see a checked box or a notice saying the account is locked out. Check the box next to "Unlock account."

6. Click Apply, then click OK.


   
## Step 4: Verify on the Client Machine

1. Go back to your Windows 11 client machine.

2. Type Sam's correct password.

3. It will instantly log him back into his desktop session normally, confirming your administrative fix worked!












