

# 🖥️ Troubleshoot GPO Not Applying

[ Back to Overview] → [README.md](https://github.com/seemasm20-source/Windows-Server-Azure-AD/blob/main/README.md)

---

## 📋 Summary

A Group Policy Object (GPO) is configured, but the setting does not take effect on a client. This file gives a checklist for finding the cause, and a reference for the two commands used most, `gpupdate` and `gpresult`.

---

## 💡 Why Might a GPO Not Apply?

A GPO reaches a user or computer only if all of these are true:

- The GPO is **linked** to the right place, and the link is enabled
- The user or computer is **inside** that OU
- **Security Filtering** allows the user or computer to receive it
- The client has **refreshed** policy, and signed in again if needed

| Policy type | Applies to | Check the OU of |
|-------------|------------|-----------------|
| **User Configuration** | User accounts | The **user** account |
| **Computer Configuration** | Computer accounts | The **computer** account |

> A new domain-joined computer lands in the default **Computers** container, and policies cannot be linked to that container. Move the computer account into an OU if a Computer Configuration policy must apply to it.

---

## 🔎 Troubleshooting Checklist

Work through the checks in order.

| Step | Check | Where | What to look for |
|:----:|-------|-------|------------------|
| 1 | Is the GPO linked to the correct OU? | Group Policy Management (`gpmc.msc`) | The GPO is listed under the OU, and **Link Enabled** says **Yes** |
| 2 | Is the user or computer in the correct OU? | Active Directory Users and Computers (ADUC) | User policy: the user is in the OU. Computer policy: the computer is in the OU |
| 3 | Does Security Filtering include the target? | GPO → **Scope** tab → **Security Filtering** | **Authenticated Users** (the default) or a group that contains the user or computer |
| 4 | Is the GPO applied or denied on the client? | `gpresult /r` | The GPO is under **Applied Group Policy Objects**, or under the list of filtered-out GPOs with a reason |
| 5 | Refresh the policy | `gpupdate /force` | "Computer Policy update has completed successfully" and the same for User Policy |
| 6 | Sign out and sign in again | The client | Some user settings, such as drive maps, apply only at sign-in. Some computer settings need a restart |

If the checks pass and the policy still does not apply, also check that the client can find the Domain Controller:

```text
C:\> nslookup seemaenterprise.co.in
```

The result should show the Domain Controller's IP address. If the client uses the wrong DNS server, it cannot download policy.

---

## 🔧 gpupdate and gpresult

### gpupdate

| Command | What it does |
|---------|--------------|
| `gpupdate` | Refreshes only the policy settings that changed |
| `gpupdate /force` | Reapplies **all** policy settings immediately. Run it on the client after any GPO change |

> By default, a client refreshes Group Policy in the background about every 90 minutes (with a random offset of up to 30 minutes). `gpupdate /force` skips the wait. Windows may ask you to sign out or restart to finish applying some settings.



---

## ✅ Verification

| Check | Command | Expected Result |
|-------|---------|-----------------|
| Policy refreshed | `gpupdate /force` | Computer and User policy updated successfully ✅ |
| GPO applied | `gpresult /r` | The GPO is listed under **Applied Group Policy Objects** ✅ |
| Setting in effect | Test on the client | The setting works, for example the USB drive is blocked ✅ |

---

## 💡 Next Step

→ [Group Policy Overview](./group-policy-overview.md)

























