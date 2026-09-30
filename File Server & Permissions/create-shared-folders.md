# 🖥️ Create Shared Folders

## Steps to do in Windows Server machine
1. Inside your Windows Server, open File Explorer and go to your C: Drive
2. Right-click an empty space, select New > Folder, and name it __Companyshare__ and create a empty file inside it.
3. Right-click Companyshare folder → Properties → Sharing tab  →  Advanced Sharing
4. Check the box that says Share this folder
5. Click Permissions button
6. Select Everyone and click Remove.
   Click Add..., type Domain Users (or your specific security group like hr-users), __User selected:sam@seemaenterprise.co.in__
7. click Check Names. Click OK.
8. Check the boxes to allow Change and Read permissions.
9. Click Apply and OK



## Steps to do in Windows Client machine /Access the File From the Windows 11 Client


1. Log into your Windows 11 Client VM as __sam@seemaenterprise.co.in__
2. Press Windows Key + R on your keyboard to open the Run dialog box.
3. Type the private network path to your server using its name or Private IP address in the UNC format
4. __\\SERVER2021\Companyshare__
   __\\172.16.0.4\Companyshare__

 5. RUN  






<img width="1920" height="1080" alt="Screenshot (608)" src="https://github.com/user-attachments/assets/9fdcd173-ab07-4877-a128-096e7e94cb4e" />






















<img width="1920" height="1080" alt="Screenshot (609)" src="https://github.com/user-attachments/assets/ed2e56f9-c6d2-427d-95c6-bbd40da7f0ca" />










































   <img width="1920" height="1080" alt="Screenshot (610)" src="https://github.com/user-attachments/assets/f775a774-0426-4107-82de-122fb1d5eb67" />







































<img width="1920" height="1080" alt="Screenshot (611)" src="https://github.com/user-attachments/assets/7e2427f0-7a1c-42cc-bdd2-0d6c98a8818d" />

















































<img width="1920" height="1080" alt="Screenshot (612)" src="https://github.com/user-attachments/assets/2030d9b7-a70b-4b7f-bb02-6908eb0fca21" />
