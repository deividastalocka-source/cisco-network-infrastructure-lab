# 7. DHCP Configuration

DHCP was configured on DC01 to provide automatic IPv4 configuration to employee workstations across the IT, Finance and HR VLANs. Separate DHCP pools were created for each department, with the appropriate network address, default gateway and DNS server information.

As DC01 is located within the server VLAN, DHCP relay was configured on the R1 subinterfaces for VLANs 10, 20 and 30 using the `ip helper-address` command. This allows DHCP requests originating from the departmental VLANs to be forwarded to DC01 at `192.168.40.10`.

DHCP functionality was verified by configuring employee workstations to obtain their network settings automatically. The clients successfully received addresses from their respective departmental address pools together with the correct subnet mask, default gateway and DNS server.

![DHCP Address Assignment](../screenshots/08%20-%20DHCP%20Address%20Assignment.png)

*Figure 8 – DHCP Address Assignment*

---

[← Previous: Inter-VLAN Routing](04-inter-vlan-routing.md) | [Next: DNS Configuration →](06-dns-configuration.md)
