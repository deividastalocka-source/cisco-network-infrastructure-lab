# 8. DNS Configuration

DNS services were configured on DC01 to provide hostname resolution across the enterprise network. An A record was created for `dc01.home.lab`, mapping the hostname to the server's static IPv4 address of `192.168.40.10`.

The DC01 address was distributed to employee workstations as their DNS server through the departmental DHCP pools. This allows devices across the IT, Finance and HR VLANs to use centralised DNS services without requiring manual DNS configuration.

DNS functionality was verified from an HR workstation using the `nslookup` command. The hostname `dc01.home.lab` successfully resolved to `192.168.40.10`. A subsequent ping using the hostname received responses from DC01 with no packet loss, confirming successful DNS resolution and network connectivity across VLANs.

![DNS Resolution Verification](../screenshots/09%20-%20DNS%20Resolution%20Verification.png)

*Figure 9 – DNS Resolution Verification*

---

[← Previous: DHCP Configuration](05-dhcp-configuration.md) | [Next: Network Security and Access Control →](07-network-security.md)
