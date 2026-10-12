
## Event ID 41 - Unexpected Shutdown

   Event ID 41 - Kernel-Power

   Log: Windows Logs → System

   Level: Critical

   Computer: LAPTOP-MN70JUKE

   BugcheckCode: 0

   SleepInProgress: 4

## Meaning: System restarted without clean shutdown

## Causes: Power cut, BSOD, overheating, hardware failure,unexpected restart.


 ## Investigate:

1. Open Event Viewer using eventvwr.msc.

2. Navigate to Windows Logs → System and find Event ID 41.

3. Check nearby events for clues about unexpected shutdowns, crashes or power interruptions.

4. Check Windows updates, device drivers, overheating and power-related issues as appropriate.
   
5. Run sfc /scannow in an elevated Command Prompt to check and repair protected Windows system files.

## Verification: Restart the computer normally and monitor whether the unexpected shutdown occurs again.

















<img width="1920" height="1080" alt="Screenshot (670)" src="https://github.com/user-attachments/assets/362fedec-676d-4198-af00-c3514657dcc2" />




























<img width="1920" height="1080" alt="Screenshot (671)" src="https://github.com/user-attachments/assets/4fc20fa9-3304-4749-b878-cec43071b2c8" />








































