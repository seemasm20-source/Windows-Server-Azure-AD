
# NTFS vs Share - which wins?

## Rule

Most restrictive permission wins.

| NTFS | Share | Effective (network) |
|------|-------|--------------------|
| Full Control | Read | Read |
| Read | Full Control | Read |
| Modify | Change | Modify |
| Deny | Full Control | Deny |


















