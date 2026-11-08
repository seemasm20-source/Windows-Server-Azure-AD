# Active Directory Users and Computers (ADUC)

## Overview

Active Directory Users and Computers (ADUC) is a management console used to manage objects within an Active Directory domain, including:

- User accounts
- Computer accounts
- Security groups
- Organizational Units (OUs)
- Domain Controller objects

ADUC was opened using:

**Server Manager → Tools → Active Directory Users and Computers**

---

## Key Concept: Organizational Units

Organizational Units (OUs) are used to organize Active Directory objects and can be used to apply Group Policies.

### Example

```text
seemaenterprise.co.in
│
├── IT
│   ├── Users
│   └── Computers
│
├── HR
│   ├── Users
│   └── Computers
│
└── Domain Controllers


## Example IT Support Tasks 

 - Using ADUC, an IT Support technician can:

-  Create and manage user accounts

 - Reset user passwords

 - Unlock locked accounts

 - Disable/enable user accounts

 - Add users to security groups

 - Locate computer accounts

 - Move computer accounts between OUs

 - Create and manage OUs

 - Check group membership


## Lab Verification

  In my Active Directory lab:

 - Domain: seemaenterprise.co.in

 - Domain Controller: server2021

 - Windows Client: Domain-joined

 - ADUC: Successfully opened

 - Computer Account: Visible in Computers
