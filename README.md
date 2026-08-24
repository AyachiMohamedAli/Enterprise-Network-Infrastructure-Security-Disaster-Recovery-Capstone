# Enterprise-Network-Infrastructure-Security-Disaster-Recovery-Capstone

**Network Administration Internship** | IT-Simplera Solutions  
**Author:** Ayachi Med Ali — Network Administration Intern

---

## Overview

Design, deployment, and verification of a secure branch-to-branch enterprise network simulated in Cisco GNS3. This project connects two branch routers over a site-to-site IPsec VPN protected by a Zone-Based Firewall (ZBF), hardened with AAA/SSH device management, secured routing via OSPF authentication, and monitored through centralized Syslog, NTP, and SNMPv3.

---

## Technologies Implemented

* **IPsec Site-to-Site VPN:** ISAKMP (IKE Phase 1), IPsec Phase 2, pre-shared keys, transform sets, and crypto maps establishing an encrypted tunnel between R-A and R-B.
* **Zone-Based Firewall (ZBF):** Security zones, zone pairs, class maps, policy maps, and service policies enforcing bidirectional traffic inspection between branches.
* **AAA Authentication + SSHv2:** Local user database, encrypted passwords, Telnet disabled, secure console/VTY access, and login banner (MOTD).
* **OSPF Authentication:** Authenticated routing adjacency between R-A and R-B with passive interfaces and prefix-list route filtering.
* **Syslog / NTP / SNMPv3:** Centralized logging, authenticated and encrypted time synchronization (`chrony`), and SNMPv3 (`authPriv`, SHA/AES) monitoring of router system data.
* **Basic Hardening:** Unused interfaces shut down, unnecessary services disabled, and administrative access restricted.

---

## Verification Highlights

* **IPsec VPN:** Tunnel established; encrypted PC-A ↔ PC-B communication confirmed.
* **Zone-Based Firewall:** ZBF policies verified in both directions without blocking legitimate traffic.
* **SSH + AAA:** Login verified from both R-A and R-B, including privileged EXEC access.
* **OSPF:** Neighbor adjacency authenticated, fully formed, and stable.
* **NTP:** `show ntp associations` and `show ntp status` confirm R-A is synchronized to the monitoring server (`sys.peer` selected).
* **SNMPv3:** `snmpwalk -v3 -l authPriv -a SHA -x AES` against R-A successfully returns full system MIB data (`sysDescr`, `sysUpTime`, `sysName`, etc.).
* **Syslog:** `rsyslogd` active and actively receiving router log messages on UDP port 514.

---



## Repository Contents

```text
├── Screenshots/                  # Verification outputs (VPN, ZBF, SSH/AAA, OSPF auth, Syslog, NTP, SNMP)
├── Router Configurations/        # Complete running configurations for R-A and R-B
├── Week8-1.gns3                 # Cisco GNS3 project file
└── Report.pdf                    # Comprehensive project documentation & troubleshooting report
