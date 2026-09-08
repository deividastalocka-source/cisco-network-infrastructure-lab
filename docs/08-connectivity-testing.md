# 10. Connectivity Testing

Connectivity testing was performed after the network infrastructure and security controls had been configured. Tests were conducted from the IT VLAN to verify communication with departmental networks and centralised server resources.

IT-PC01 successfully communicated with devices across the Finance and HR VLANs and reached DC01 within the server VLAN. The workstation also successfully resolved and contacted `dc01.home.lab`, confirming that inter-VLAN routing, DHCP-provided network configuration and DNS services were operating correctly.

Additional testing confirmed that the access control policies remained operational, with communication between the Finance and HR VLANs restricted while both departments retained access to required server resources.

![Network Connectivity Verification](../screenshots/11%20-%20Network%20Connectivity%20Verification.png)

*Figure 11 – Network Connectivity Verification*

---

[← Previous: Network Security and Access Control](07-network-security.md) | [Next: Troubleshooting Scenarios →](09-troubleshooting.md)
