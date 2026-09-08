# 12. Conclusion

The Cisco Network Infrastructure Lab successfully demonstrated the design, configuration and testing of a segmented business network using Cisco networking technologies. The environment was divided into dedicated IT, Finance, HR and Server VLANs to provide logical separation between departments.

Inter-VLAN routing was implemented using router-on-a-stick, allowing controlled communication between VLANs. Centralised DHCP and DNS services were configured through DC01, with DHCP relay enabling workstations across multiple VLANs to automatically obtain their network configuration. Access Control Lists were also implemented to restrict direct communication between the Finance and HR networks while maintaining access to shared server resources and unrestricted administrative connectivity from the IT VLAN.

Network functionality was verified through connectivity, DHCP and DNS testing. Troubleshooting scenarios involving an incorrect VLAN assignment, default gateway and DNS configuration were then introduced and successfully resolved.

---

# 13. Lessons Learned

This project provided practical experience in designing, configuring and troubleshooting a segmented enterprise network. Building the environment demonstrated how VLANs can be used to separate departments while trunk links allow VLAN traffic to move between network devices.

Configuring router-on-a-stick provided a better understanding of how inter-VLAN routing enables communication between separate networks. Implementing DHCP relay also demonstrated how a centralised DHCP server can provide addressing information to clients located outside its local subnet.

The implementation of Access Control Lists highlighted the importance of considering all required network traffic when applying security controls. During testing, the Finance and HR ACLs initially prevented clients from obtaining DHCP leases because the rules did not account for DHCP traffic from devices without an assigned IP address. Diagnosing and correcting this issue demonstrated how security configurations can unintentionally affect network services.

The troubleshooting scenarios further developed a structured approach to diagnosing connectivity problems. Checking VLAN assignments, IP addressing, default gateways, DNS configuration and connectivity at different stages helped isolate each fault before applying a solution.

Overall, the project strengthened practical knowledge of **Cisco IOS, VLANs, trunking, routing, DHCP, DNS, ACLs, network segmentation and troubleshooting**, while demonstrating how these technologies work together within an enterprise network.

---

[← Previous: Troubleshooting Scenarios](09-troubleshooting.md) | [Back to README](../README.md)
