### Role installation and domain creation

- Created a domain account on DC01 (domain name: ad.ironwood.test;
short:IRONWOOD)
- Joined MEMBER01 to domain ad.ironwood.test
    - used DC01's private address as the only DNS server adress for MEMBER01
    - checked DNS server of MEMBER01 `Get-DnsClientServerAddress -AddressFamily IPv4` and checked with `Resolve-DnsName -Type SRV _ldap._tcp.dc._msdcs.ad.ironwood.test -Server 10.40.0.4` who runs the domain
    ![](assets/validation-ip-owner.png)
