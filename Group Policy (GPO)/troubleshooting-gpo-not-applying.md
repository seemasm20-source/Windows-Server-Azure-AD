
# Troubleshoot GPO Not Applying

1. GPO linked to correct OU? → GPMC check
2. User in correct OU? → ADUC check
3. Security Filtering → Authenticated Users listed?
4. gpresult /r → Applied or Denied?
5. gpupdate /force → try again
6. Log off and on → some User Config needs login


# gpupdate and gpresult

 ## gpupdate /force

    Forces immediate refresh of all Group Policies  / Run on client after any GPO change

## gpresult /r

   Shows which GPOs apply to current user and machine

## gpresult /h C:\gpresult.html

  Exports full GPO report as HTML
