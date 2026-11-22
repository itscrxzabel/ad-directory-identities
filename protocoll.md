### Role installation and domain creation

- Created a domain account on DC01 (domain name: ad.ironwood.test;
short:IRONWOOD)
- Joined MEMBER01 to domain ad.ironwood.test
    - used DC01's private address as the only DNS server adress for MEMBER01
    - checked DNS server of MEMBER01 `Get-DnsClientServerAddress -AddressFamily
    IPv4` and checked domain owner `Resolve-DnsName -Type SRV
    _ldap._tcp.dc._msdcs.ad.ironwood.test -Server 10.40.0.4`

![](assets/validation-ip-owner.png)

### Creation of Organizational Units

![OUs created under Ironwood](assets/organisational-units.png)

- Command for listing the OUs in Windows Powershell: `Get-ADOrganizationalUnit
-Filter * -SearchBase "OU=Ironwood,DC=ad,DC=ironwood,DC=test" -Properties
ProtectedFromAccidentalDeletion | Select-Object Name, DistinguishedName,
ProtectedFromAccidentalDeletion`

![List of OU in Ironwood](assets/powershell-OU-list.png)

- All OUs deletion protected

### Creation of Account Maja

- Created user Maja Chen in Operations OU

![](assets/user-maja.chen)

- Added organizational details for Maja Chen

![](assets/organisational-details-maja.chen)

- Checked user details of maya.chen `Get-ADUser maya.chen -Properties
DisplayName, Department, UserPrincipalName, Enabled | Select-Object Name,
DisplayName, SamAccountName, UserPrincipalName, Department, Enabled,
DistinguishedName, SID, ObjectGUID`
- Important identifieres of maya.chen (SID:
S-1-5-21-4180911846-3264414346-1653429677-1601, ObjectGUID: 774dea48-7376-44a5-94b5-b298fb74dd20)


### Allowing User Maja Chen to login at Server MEMBER01

- I have added maya.chen to the remote desktop users (compmgmt.msc >
system.tools > local users and groups > groups > rdp) in order for her to be
able to login to the server MEMBER01

![](assets/rdpallowance-maya.chen)

- Logged into Server MEMBER01 with maya.chen's credentials (Username:
IRONWOOD\maya.chen; Password)
- Checked if account details are correct: `whoami`, `hostname`, `whoami /user`,
  `whoami /groups`
    - `whoami /user` SID identical to the one mentioned earlier: Identification
      of user maya.chen successful

![](assets/maya.chen-usercheck)

### Moving user Maya Chen to the OU Finance
