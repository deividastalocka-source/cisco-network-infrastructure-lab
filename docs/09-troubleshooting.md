# 11. Troubleshooting Scenarios

Three troubleshooting scenarios were performed to simulate common network configuration issues and demonstrate a structured approach to identifying, diagnosing and resolving connectivity problems.

## 11.1 Incorrect VLAN Assignment

A VLAN configuration fault was intentionally introduced by assigning the switch port connected to IT-PC02 to VLAN 20 instead of VLAN 10. Following the configuration change, IT-PC02 was unable to communicate with its default gateway at `192.168.10.1`.

The switch configuration was inspected using Cisco IOS commands, which identified that FastEthernet0/3 on SW2-IT had been incorrectly assigned to VLAN 20.

![Incorrect VLAN Assignment and Connectivity Failure](../screenshots/12%20-%20VLAN%20Troubleshooting%20Issue.png)

*Figure 12 – Incorrect VLAN Assignment and Connectivity Failure*

FastEthernet0/3 was reassigned to VLAN 10 and connectivity was tested again. IT-PC02 successfully communicated with its default gateway, confirming that normal connectivity had been restored.

![VLAN Configuration Corrected and Connectivity Restored](../screenshots/13%20-%20VLAN%20Troubleshooting%20Resolution.png)

*Figure 13 – VLAN Configuration Corrected and Connectivity Restored*

---

## 11.2 Incorrect Default Gateway

A second fault was introduced on FIN-PC01 by changing its default gateway from `192.168.20.1` to the incorrect address `192.168.20.254`.

Although the workstation remained configured within the Finance subnet, it could no longer communicate with DC01 on the Server VLAN because traffic destined for remote networks could not be forwarded through the correct router interface.

![Incorrect Default Gateway and Connectivity Failure](../screenshots/14%20-%20Incorrect%20Default%20Gateway.png)

*Figure 14 – Incorrect Default Gateway and Connectivity Failure*

The workstation's network configuration was inspected and the incorrect gateway was identified. The default gateway was restored to `192.168.20.1`, after which connectivity to DC01 at `192.168.40.10` was successfully verified.

![Default Gateway Corrected and Connectivity Restored](../screenshots/15%20-%20Default%20Gateway%20Troubleshooting%20Resolution.png)

*Figure 15 – Default Gateway Corrected and Connectivity Restored*

---

## 11.3 DNS Resolution Failure

The final troubleshooting scenario simulated a DNS configuration fault on HR-PC02. The DNS server was changed from the correct address `192.168.40.10` to the incorrect address `192.168.40.254`.

Connectivity to DC01 using its IP address remained operational, demonstrating that network connectivity and inter-VLAN routing were functioning correctly. However, attempts to resolve `dc01.home.lab` failed, isolating the issue to DNS rather than general network connectivity.

![Incorrect DNS Configuration and Name Resolution Failure](../screenshots/16%20-%20DNS%20Resolution%20Failure.png)

*Figure 16 – Incorrect DNS Configuration and Name Resolution Failure*

The DNS server address was restored to `192.168.40.10`. DNS resolution was then verified using `nslookup` and by successfully communicating with `dc01.home.lab`.

![DNS Configuration Corrected and Name Resolution Restored](../screenshots/17%20-%20DNS%20Troubleshooting%20Resolution.png)

*Figure 17 – DNS Configuration Corrected and Name Resolution Restored*

---

These scenarios demonstrate troubleshooting across three different areas of the network: **VLAN configuration, IP addressing and DNS resolution**. Each fault was identified using network diagnostic tools, corrected and followed by connectivity testing to verify successful remediation.

---

[← Previous: Connectivity Testing](08-connectivity-testing.md) | [Next: Conclusion and Lessons Learned →](10-lessons-learned.md)
