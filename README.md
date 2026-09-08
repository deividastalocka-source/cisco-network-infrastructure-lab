# Cisco Network Infrastructure Lab

A Cisco Packet Tracer network lab designed to simulate a segmented business network across IT, Finance, HR and Server departments.

The project demonstrates the configuration of VLANs, 802.1Q trunking, inter-VLAN routing, DHCP, DNS, Access Control Lists (ACLs) and network troubleshooting using Cisco networking technologies.

## Network Topology

![Network Topology](screenshots/01%20-%20Initial%20Network%20Topology.png)

## Project Overview

The network was designed around a central Cisco router and core switch, with separate access switches providing connectivity for the IT, Finance and HR departments.

Four VLANs were implemented to logically separate departmental traffic and server infrastructure:

| VLAN | Department | Network | Default Gateway |
|---:|---|---|---|
| 10 | IT | `192.168.10.0/24` | `192.168.10.1` |
| 20 | Finance | `192.168.20.0/24` | `192.168.20.1` |
| 30 | HR | `192.168.30.0/24` | `192.168.30.1` |
| 40 | Servers | `192.168.40.0/24` | `192.168.40.1` |

DC01 was configured with the static address `192.168.40.10` and provides centralised DHCP and DNS services to the network.

## Technologies & Concepts

- Cisco Packet Tracer
- Cisco IOS
- VLANs
- 802.1Q trunking
- Router-on-a-stick
- Inter-VLAN routing
- IPv4 addressing and subnetting
- DHCP
- DHCP relay
- DNS
- Extended Access Control Lists (ACLs)
- Network segmentation
- Network troubleshooting

## Key Features

### Network Segmentation
Separate VLANs were configured for the IT, Finance, HR and Server networks, providing logical separation between departments.

### Inter-VLAN Routing
Router-on-a-stick was configured on R1 using 802.1Q subinterfaces to provide communication between the four VLANs.

### Centralised DHCP
DC01 provides DHCP services for the IT, Finance and HR networks. DHCP relay was configured on R1 to forward requests between VLANs and the central DHCP server.

### DNS
DC01 provides internal DNS services, including the `dc01.home.lab` record mapped to `192.168.40.10`.

### Access Control
Extended ACLs were implemented to prevent direct communication between the Finance and HR networks while maintaining access to required server resources. The IT VLAN retains unrestricted administrative connectivity.

### Troubleshooting
Three network faults were intentionally introduced, diagnosed and resolved:

1. Incorrect VLAN assignment
2. Incorrect default gateway
3. DNS resolution failure

During implementation, an additional DHCP issue caused by the Finance and HR ACLs was identified and resolved by explicitly permitting DHCP traffic.

## Documentation

Detailed documentation for the complete implementation is available within the `docs` directory.

| Section | Documentation |
|---|---|
| 1 | [Lab Environment](docs/01-lab-environment.md) |
| 2 | [Network Infrastructure Configuration](docs/02-network-infrastructure.md) |
| 3 | [VLAN Configuration](docs/03-vlan-configuration.md) |
| 4 | [Inter-VLAN Routing](docs/04-inter-vlan-routing.md) |
| 5 | [DHCP Configuration](docs/05-dhcp-configuration.md) |
| 6 | [DNS Configuration](docs/06-dns-configuration.md) |
| 7 | [Network Security and Access Control](docs/07-network-security.md) |
| 8 | [Connectivity Testing](docs/08-connectivity-testing.md) |
| 9 | [Troubleshooting Scenarios](docs/09-troubleshooting.md) |
| 10 | [Conclusion and Lessons Learned](docs/10-lessons-learned.md) |

## Troubleshooting Highlights

The project included practical troubleshooting across multiple areas of the network.

### VLAN Assignment

IT-PC02 was intentionally assigned to the incorrect VLAN, preventing communication with its default gateway. The issue was identified through Cisco IOS verification commands and resolved by restoring the switch port to VLAN 10.

### Default Gateway

FIN-PC01 was configured with an incorrect default gateway, preventing communication outside its local subnet. Restoring the correct gateway re-established connectivity to DC01.

### DNS Resolution

HR-PC02 was configured with an incorrect DNS server. IP connectivity remained operational while hostname resolution failed, allowing the issue to be isolated specifically to DNS.

### ACL and DHCP

During testing, the Finance and HR ACLs initially prevented clients from obtaining DHCP leases because DHCP traffic from devices without an assigned IP address was not accounted for. The ACLs were corrected to explicitly permit DHCP traffic before applying the remaining access control rules.

## Repository Structure

```text
cisco-network-infrastructure-lab/
│
├── README.md
├── LICENSE
│
├── docs/
│   ├── 01-lab-environment.md
│   ├── 02-network-infrastructure.md
│   ├── 03-vlan-configuration.md
│   ├── 04-inter-vlan-routing.md
│   ├── 05-dhcp-configuration.md
│   ├── 06-dns-configuration.md
│   ├── 07-network-security.md
│   ├── 08-connectivity-testing.md
│   ├── 09-troubleshooting.md
│   └── 10-lessons-learned.md
│
├── packet-tracer/
│   └── Lab.pkt
│
└── screenshots/
    ├── 01 - Initial Network Topology.png
    ├── 02 - Physical Network Connections.png
    ├── ...
    └── 17 - DNS Troubleshooting Resolution.png
