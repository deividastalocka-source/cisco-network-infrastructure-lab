# 3. Lab Environment

## 3.1 Network Topology

The initial network topology was created in Cisco Packet Tracer to represent the organisation's enterprise network. A Cisco router and core switch provide the central network infrastructure, with separate access switches allocated to the IT, Finance and HR departments. A dedicated server represents the DC01 infrastructure server used throughout the environment.

![Initial Enterprise Network Topology](../screenshots/01.png)

*Figure 1 – Initial Enterprise Network Topology*

---

## 3.2 Network Devices

The simulated enterprise environment consists of Cisco networking equipment, departmental workstations and a centralised infrastructure server. R1 provides Layer 3 routing between the network segments, while SW1-CORE acts as the central switching point connecting the router, server and departmental access switches.

Three Cisco 2960 access switches provide connectivity for the IT, Finance and HR departments. Each departmental switch connects two employee workstations to its respective VLAN. DC01 is connected directly to the core switch and provides centralised DHCP and DNS services to devices throughout the network.

The network consists of the following devices:

| Device | Role |
|---|---|
| **R1** | Router providing inter-VLAN routing and access control |
| **SW1-CORE** | Core switch connecting the network infrastructure |
| **SW2-IT** | Access switch for the IT department |
| **SW3-FINANCE** | Access switch for the Finance department |
| **SW4-HR** | Access switch for the HR department |
| **DC01** | Central DHCP and DNS server |
| **IT-PC01 / IT-PC02** | IT employee workstations |
| **FIN-PC01 / FIN-PC02** | Finance employee workstations |
| **HR-PC01 / HR-PC02** | HR employee workstations |

---

## 3.3 VLAN and IP Addressing Scheme

The network was segmented into four VLANs to separate departmental traffic and server infrastructure. Each VLAN was assigned a dedicated `/24` IPv4 subnet, providing logical separation between the IT, Finance, HR and server networks.

The first usable address within each subnet was assigned to the corresponding R1 subinterface and acts as the default gateway for devices within that VLAN. Employee workstations receive their IPv4 configuration dynamically through DHCP, while DC01 uses a static address to ensure that centralised network services remain consistently available.

| VLAN | Name | Network | Default Gateway | Addressing |
|---|---|---|---|---|
| **10** | IT | `192.168.10.0/24` | `192.168.10.1` | DHCP |
| **20** | Finance | `192.168.20.0/24` | `192.168.20.1` | DHCP |
| **30** | HR | `192.168.30.0/24` | `192.168.30.1` | DHCP |
| **40** | Servers | `192.168.40.0/24` | `192.168.40.1` | Static |

DC01 was assigned the static IPv4 address `192.168.40.10/24` within VLAN 40. Employee DHCP pools begin at `.100` within their respective departmental subnets.

---

## 3.4 Network Services

Centralised network services were provided by DC01 within the server VLAN. The server was assigned the static IPv4 address `192.168.40.10` to provide a consistent destination for client devices and network infrastructure.

DHCP was configured to automatically provide IPv4 addressing information to workstations within the IT, Finance and HR VLANs. Separate DHCP pools were created for each department, providing the appropriate IP address range, subnet mask, default gateway and DNS server configuration. DHCP relay was configured on R1 to forward requests between the departmental VLANs and DC01.

DNS was also configured on DC01 to provide hostname resolution across the network. The internal DNS record `dc01.home.lab` was mapped to `192.168.40.10`, allowing employee workstations to locate the server using its hostname rather than its IPv4 address.

| Service | Host | Address | Purpose |
|---|---|---|---|
| **DHCP** | DC01 | `192.168.40.10` | Dynamic IPv4 configuration |
| **DNS** | DC01 | `192.168.40.10` | Internal hostname resolution |
| **Inter-VLAN Routing** | R1 | `.1` on each subnet | Communication between VLANs |
| **DHCP Relay** | R1 | VLAN 10/20/30 subinterfaces | Forwards DHCP requests to DC01 |

---

[Next: Network Infrastructure Configuration →](02-network-infrastructure.md)
