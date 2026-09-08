# 5. VLAN Configuration

VLANs were configured to logically separate the organisation's departments and server infrastructure. Four VLANs were created on the core switch to represent the IT, Finance, HR and server network segments.

VLAN 10 was assigned to IT, VLAN 20 to Finance, VLAN 30 to HR and VLAN 40 to server infrastructure. The DC01 server connection was assigned to VLAN 40 to place the server within its dedicated network segment.

The VLAN configuration was verified through the Cisco IOS command-line interface to confirm that each VLAN had been successfully created and was active.

![Core Switch VLAN Configuration](../screenshots/04%20-%20Core%20Switch%20VLAN%20Creation.png)

*Figure 4 – Core Switch VLAN Configuration*

Trunk links were then configured between the core switch and the three departmental access switches. The FastEthernet0/1, FastEthernet0/2 and FastEthernet0/3 interfaces on SW1-CORE were configured as 802.1Q trunks, allowing VLANs 10, 20, 30 and 40 to traverse the links.

The trunk configuration was verified using the `show interfaces trunk` command. All three interfaces were confirmed to be operating in trunking mode, with VLANs 10, 20, 30 and 40 allowed and active across the trunk connections.

![Core Switch Trunk Configuration](../screenshots/05%20-%20Core%20Switch%20Trunk%20Configuration.png)

*Figure 5 – Core Switch Trunk Configuration*

The departmental access switches were configured to place employee workstations within their appropriate VLANs. The IT workstations were assigned to VLAN 10, Finance workstations to VLAN 20 and HR workstations to VLAN 30.

The uplink interface on each departmental switch was configured as an 802.1Q trunk to allow communication with the core switch. The trunk links were restricted to VLANs 10, 20, 30 and 40 to ensure that only the required VLAN traffic could traverse the network infrastructure.

The configuration was verified using the `show vlan brief` and `show interfaces trunk` commands to confirm that access ports were assigned correctly and that the uplink interfaces were operating in trunking mode.

![Access Switch VLAN and Trunk Configuration](../screenshots/06%20-%20Departmental%20Switch%20VLAN%20Configuration.png)

*Figure 6 – Access Switch VLAN and Trunk Configuration*

---

[← Previous: Network Infrastructure Configuration](02-network-infrastructure.md) | [Next: Inter-VLAN Routing →](04-inter-vlan-routing.md)
