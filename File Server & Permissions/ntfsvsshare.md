
# NTFS vs Share.

 Rule - Share Permissions + NTFS Permissions = Most Restrictive Result

Most restrictive permission wins.

| NTFS | Share | Effective (network) |
|------|-------|--------------------|
| Full Control | Read | Read |
| Read | Full Control | Read |
| Modify | Change | Modify |
| Deny | Full Control | Deny |


















