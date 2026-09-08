# 6. Inter-VLAN Routing

Inter-VLAN routing was configured using a router-on-a-stick architecture to enable communication between the separate VLANs. The GigabitEthernet0/0 interface on R1 was divided into four logical subinterfaces, with each subinterface associated with a specific VLAN using IEEE 802.1Q encapsulation.

The subinterfaces were assigned the addresses `192.168.10.1`, `192.168.20.1`, `192.168.30.1` and `192.168.40.1` for the IT, Finance, HR and server VLANs respectively. These addresses provide the default gateways for devices within each network segment.

The configuration was verified using the `show ip interface brief` command. All four router subinterfaces were confirmed to be operational with both the interface status and line protocol showing as up.

![Inter-VLAN Routing Configuration](../screenshots/07%20-%20Inter-VLAN%20Routing%20Configuration.png)

*Figure 7 – Inter-VLAN Routing Configuration*

---
 
[← Previous: VLAN Configuration](03-vlan-configuration.md) | [Next: DHCP Configuration →](05-dhcp-configuration.md)
