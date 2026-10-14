
# UNC Path Access 

A Universal Naming Convention (UNC) path identifies a shared network resource using the format:

`\\ComputerName\ShareName`

* **ComputerName:** The hostname or IP address of the computer hosting the share.
* **ShareName:** The name assigned to the shared folder.

UNC paths allow users and IT support technicians to access network folders without needing to know the folder's local disk path.


## Environment

* **Platform:** Microsoft Azure
* **Client:** Windows Client VM
* **File server:** Windows Server VM (`server2021`)
* **Protocol:** SMB
* **Default SMB port:** TCP 445
* **Example UNC path:** `\\server2021\Companyshare`



## Steps to Connect

1. Sign in to the Windows Client VM.

2. Confirm that the client can resolve the server hostname.

3. Press `Win + R` to open the Run dialog.

4. Enter the UNC path of an existing shared folder, for example:

   `\\server2021\Companyshare`

5. Press Enter and authenticate with an authorised domain account if prompted.

6. Confirm whether the shared folder opens.

7. If access is denied or the path is unavailable, record the error message and troubleshoot.

## Troubleshooting Scenarios

* **Network path not found:** Verify the server name, share name, network connectivity and SMB availability.
* **Access denied:** Check both share permissions and NTFS permissions.
* **Credentials rejected:** Verify the username, password and domain account status.
* **Hostname not resolving:** Check DNS settings and test name resolution.
* **SMB connection blocked:** Check Windows Firewall and Azure network security rules for TCP 445 between the relevant machines.
* **Mapped drive unavailable:** Test the UNC path directly to determine whether the issue is with the share or the drive mapping.

## Permissions to Check

* **Share permissions:** Control access through the network share.
* **NTFS permissions:** Control access to files and folders on the underlying NTFS volume.
* **Effective network access:** Both sets of permissions apply; the more restrictive combination determines the user's access.

## Verification

* Confirm that the authorised user can open the shared folder.
* Test whether the user can perform the permitted actions, such as reading or creating a test file.
* If access fails, identify the cause, apply an appropriate fix and retest.
* Record the result without including passwords or sensitive data.






<img width="2100" height="2673" alt="0387A8B0-9744-4602-9F85-ECC380DEF566" src="https://github.com/user-attachments/assets/6dac9dd3-d351-400c-a283-b150c1e998df" />


