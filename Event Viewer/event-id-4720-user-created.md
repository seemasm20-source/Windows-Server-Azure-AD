
## Event ID 4720 - User Account Created

  __Log: Security__

  __New Account Name: ziggy__

 __Subject Account: Administrator__

 __Status: Audit Success__

 __Location: Windows Server (Domain Controller Only)__



1. Log into your Windows Server Domain Controller (server2021).

2. Open Active Directory Users and Computers (dsa.msc)

3. Right-click your target Organization Unit (e.g., SALES OU), select New, and click User.

4. Fill in the details for a new user account (e.g., Name: ziggy, Logon Name: ziggy) and click Finish.

5. Result: This action instantly writes an Event ID 4720 to the Server's Security log, naming Administrator as the creator and ziggy as the new account.




<img width="1920" height="1080" alt="Screenshot (667)" src="https://github.com/user-attachments/assets/fcc49f1b-1d91-4e81-9fbe-ffb8bc25fce9" />




































<img width="1920" height="1080" alt="Screenshot (669)" src="https://github.com/user-attachments/assets/01979d91-ad93-46c3-a94e-7c7c51bd39c6" />
