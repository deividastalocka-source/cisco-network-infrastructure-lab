# 9. Network Security and Access Control

Extended access control lists were configured on R1 to restrict communication between the Finance and HR network segments. The security policy prevents Finance devices from initiating communication with the HR VLAN and prevents HR devices from initiating communication with the Finance VLAN, while maintaining access to required server resources.

The `FINANCE-ACL` was applied inbound to the VLAN 20 router subinterface, while the `HR-ACL` was applied inbound to the VLAN 30 subinterface. Each ACL denies traffic destined for the opposing departmental network before permitting other required traffic. DHCP traffic was explicitly permitted within the ACLs to ensure that clients could obtain network configuration from the centralised DHCP server before the remaining access control rules were evaluated.

The access control configuration was tested from departmental workstations. Communication between the HR and Finance VLANs was successfully blocked, while connectivity from HR to DC01 at `192.168.40.10` remained operational. This confirmed that the ACLs provided departmental network isolation without preventing access to centralised services.

![ACL Connectivity Verification](../screenshots/10%20-%20ACL%20Connectivity%20Verification.png)

*Figure 10 – ACL Connectivity Verification*

---

[← Previous: DNS Configuration](06-dns-configuration.md) | [Next: Connectivity Testing →](08-connectivity-testing.md)
