# Active Directory Lab — Ironwood

A self-built Windows Server lab covering the basics of Active Directory administration: standing up a domain, joining a member server, designing an OU structure, and working through the full lifecycle of a user account — create, move, disable, re-enable, troubleshoot.

The focus is on verifying every change rather than assuming it worked, and on tracking identity by SID instead of by name.

## Environment

| Component | Value |
| --- | --- |
| Domain | `ad.ironwood.test` (NetBIOS: `IRONWOOD`) |
| Domain controller | `DC01` (`10.40.0.4`) |
| Member server | `MEMBER01`, DNS pointed at `DC01` |
| Test user | `IRONWOOD\maya.chen` |

## Covered in this lab

- AD DS installation and domain creation
- Domain join with DNS as the precondition; domain owner verified via `_ldap._tcp.dc._msdcs` SRV records
- OU structure with accidental-deletion protection enabled
- User provisioning with organizational attributes, and granting interactive logon on a member server
- Moving a user between OUs — what changes (DN, GPO scope, delegation) and what doesn't (SID, group memberships)
- Disable-and-park instead of delete, so permissions tied to the SID stay intact
- Troubleshooting a failed logon: one `Get-ADUser` query explained both a disabled account and an unexpected OU, and ruled out a password reset as unnecessary

## Documentation

The full step-by-step walkthrough — commands, output and screenshots — is in **[protocoll.md](protocoll.md)**.

---

*All domain names, addresses and accounts belong to an isolated test lab and do not exist outside it.*
