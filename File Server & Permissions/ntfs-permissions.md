
NTFS File Sharing & Permissions:

NTFS stands for New Technology File System. It is the standard file system used by modern Windows operating systems to store and manage files and folders.

NTFS permissions control which users and groups can access files and folders and what actions they can perform, such as Read, Write, Modify, or Full Control.

When a folder is shared over a network, users can access it using a UNC path such as: \\server2021\CompanyData


Key NTFS Permissions: 

| Permission     | Description                                  |
| -------------- | -------------------------------------------- |
| Full Control   | Read, modify, delete, and change permissions |
| Modify         | Read, write, modify, and delete              |
| Read & Execute | View files and execute programs              |
| Read           | View and open files                          |
| Write          | Create or modify files                       |







Create NTFS File Sharing Permissions:

Steps to do in Windows Server machine:-


1. Create the Subfolder
2. On your Windows Server, open File Explorer and navigate into C:\CompanyShare.
3. Right-click an empty space, choose New > Folder, and name it Finance . Inside Finance create a file/doc by name IT doc
4. Open the Security Settings
5. Right-click your new Finance folder and select Properties.
6.  Switch to the Security tab at the top.
   
4. Set Specific NTFS Permissions for the User "__SAM__" for __READ & EXECUTE PERMISSION__

Now back on the main Security tab screen:

1. Click the Edit... button.
2. Click Add..., type __SAM__, and click Check Names. Then click OK.
3. With __SAM__ highlighted in the top box, go to the bottom box and check the box for __READ & EXECUTE__. (This automatically checks Read and List folder contents, allowing him       to view  files).
4. Click Add... again, type __SAM__ and click Check Names. Then click OK.
5. Check whether access is given for __READ & EXECUTE__ in client machine

Set Specific NTFS Permissions for the User "__SAM__" for __MODIFY PERMISSION__

1. Click the Edit... button.
2. Click Add..., type __SAM__, and click Check Names. Then click OK.
3. With __SAM__ highlighted in the top box, go to the bottom box and check the box for __MODIFY__. (This automatically checks Read, Write, and List folder contents, allowing him to create and edit files).
4. Click Add... again, type __SAM__ and click Check Names. Then click OK.
5. Check whether access is given for __MODIFY__
6. Click Apply and OK to close all properties windows.




Steps to do in Windows Client machine:-



1. Log into the Windows 11 Client as sam. Open the share via \\172.16.0.4\CompanyShare\Finance. Try to right-click and get in to IT doc text file and read ,
2. Windows 11 will show a popup saying    "Destination Folder Access Denied" because his NTFS permission is Read Only.

3. Log out and sign back in as ganesha. Go to the same folder. He will be able to create, write, and delete files perfectly because his NTFS permission is set to Modify.







