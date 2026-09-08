# 4. Network Infrastructure Configuration

The network devices were connected using Ethernet connections to establish the physical topology. Each departmental access switch was connected to the core switch, while employee workstations were connected to their respective departmental switches. DC01 was connected directly to the core switch to provide centralised server connectivity across the network.

![Physical Network Connections](../screenshots/02%20-%20Physical%20Network%20Connections.png)

*Figure 2 – Physical Network Connections*

The R1 router was configured through the Cisco IOS command-line interface. The GigabitEthernet0/0 interface connecting R1 to the core switch was enabled using the `no shutdown` command. Interface status was then verified to confirm that both the physical interface and line protocol were operational.

![Router Interface Verification](../screenshots/03%20-%20Router%20Interface%20Verification.png)

*Figure 3 – Router Interface Verification*

---

[← Previous: Lab Environment](01-lab-environment.md) | [Next: VLAN Configuration →](03-vlan-configuration.md)
