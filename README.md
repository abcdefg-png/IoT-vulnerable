# IoT Vulnerability Research Report

## Overview

Our research team has conducted an extensive security analysis on IoT devices from multiple vendors. Through systematic vulnerability discovery and responsible disclosure, we have identified a large number of security issues and obtained **CVE** identifiers for the vast majority of them.

<div align="center">
<table>
<tr>
<td align="center" width="200">
<br>
<h1>20</h1>
<b>🏭 Vendors Affected</b>
<br><br>
</td>
<td align="center" width="200">
<br>
<h1>133</h1>
<b>📡 Device Firmwares</b>
<br><br>
</td>
<td align="center" width="200">
<br>
<h1>908</h1>
<b>🏷️ CVEs Assigned</b>
<br><br>
</td>
</tr>
</table>
</div>

---

## 📚 Related Publications

Our vulnerability discovery work is supported by the following research papers:

- **IoTBec: An Accurate and Efficient Recurring Vulnerability Detection Framework for Black Box IoT Devices**
  *NDSS 2026* | **CCF-A**

- **Bridge: High-Order Taint Vulnerabilities Detection in Linux-based IoT Firmware**
  *IEEE S&P 2026* | **CCF-A**

- **Bond: Constraint-Directed Fuzzing for Automated Validation of Taint Analysis  Results in Linux-based IoT Firmware**
  *USENIX Security 2026* | **CCF-A**

- **LoopSCC: Summarizing Complex Multi-branch Nested Loops via Periodic Oscillation Interval**
  *ICSE 2026* | **CCF-A**

- **FalconScope: Effective and Efficient Detection of Hidden Web Interfaces in IoT Devices**
  *WWW 2026* | **CCF-A**

- **Hidden and Lost Control: on Security Design Risks in IoT User-Facing Matter Controller**
  *NDSS 2025* | **CCF-A**

- **FirmSV: Detecting Stored Vulnerabilities in IoT Firmware using Static Taint Analysis**
  *CSCWD 2026* | CCF-C

<sub>*Papers under submission: ASE, TDSC*</sub>

## Summary by Vendor

| Vendor | Affected Firmwares | CVEs Assigned |
| :---: | :---: | :---: |
| **Tenda** | 37 | 418 |
| **TOTOLINK** | 25 | 136 |
| **D-Link** | 30 | 159 |
| **TP-LINK** | 6 | 8 |
| **Linksys** | 8 | 61 |
| **NETGEAR** | 17 | 63 |
| **Motorola** | 1 | 1 |
| **Cisco** | 4 | 35 |
| **ARRIS** | 4 | 13 |
| **Belkin** | 1 | 14 |
| **Total** | **133** | **908** |
| 🟣 **Matter Protocol** | 10 vendors | confirmed by vendor |

---

## Vulnerability Type Distribution

| Vulnerability Type | Description |
| :--- | :--- |
| 💥 **Buffer Overflow** | The most prevalent type, accounting for the majority of all findings |
| 💉 **Command Injection** | Remote command execution through improperly sanitized inputs |
| 🔓 **Improper Access Controls** | Unauthorized access to restricted functionalities |
| 📂 **Information Disclosure** | Exposure of sensitive device or configuration data |
| 🔑 **Hard-Coded Password** | Embedded credentials in firmware |
| 🔄 **CSRF** | Cross-Site Request Forgery enabling unauthorized actions |
| 🟣 **UMCCI Flaws** | User-facing Matter control capabilities and interfaces flaws in Matter protocol implementations |

---

## Detailed Findings by Vendor

### <img src="https://img.shields.io/badge/Matter%20Protocol-10%20Vendors-blueviolet?style=for-the-badge" alt="Matter Protocol">

We reveal a new kind of design flaw in user-facing Matter control capabilities and interfaces, called UMCCI flaws, which are exploitable vulnerabilities in the design space and seriously jeopardize necessary control and surveillance capabilities of Matter-enabled devices for IoT users.

<details>
<summary><b>📡 Affected Vendors (Click to Expand)</b></summary>

- Apple
- Samsung
- Xiaomi
- Amazon
- Tuya
- Uascent
- Aqara
- Signify
- VIVO
- Electro Cirkel Retail B.V.

</details>

---

### <img src="https://img.shields.io/badge/Tenda-418%20CVEs-red?style=for-the-badge" alt="Tenda">

We discovered security issues across **37** different device firmwares from **Tenda**, obtaining a total of **418 CVEs**.

<details>
<summary><b>📡 Affected Product Lines (Click to Expand)</b></summary>

- 4G300, A18, AC10Uv1.0, AC10v4.0, AC15, AC18, AC23, AC5, AC500, AC6, AC7V1.0, AC8v4, AC9, AX12, AX1803, AX1806, AX3, F1202, F1203, FH1201, FH1202, FH1203, FH1205, FH1206, G1, G3, O1, O3V2.0, O5V1.0, O6, TX9, W15EV1.0, W20EV4.0, W30Ev1.0, W9, i21, i22

</details>

<details>
<summary><b>🏷️ CVE Breakdown by Type (Click to Expand)</b></summary>

| Category | CVEs |
| :--- | :---: |
| Buffer Overflow | 367 |
| Command Injection | 36 |
| Improper Access Controls | 10 |
| CSRF | 5 |
| Information Disclosure | 2 |
| **Total** | **418** |

</details>

---

### <img src="https://img.shields.io/badge/TOTOLINK-136%20CVEs-orange?style=for-the-badge" alt="TOTOLINK">

We discovered security issues across **25** different device firmwares from **TOTOLINK**, obtaining a total of **136 CVEs**.

<details>
<summary><b>📡 Affected Product Lines (Click to Expand)</b></summary>

- A3000RU, A3002R, A3100R, A3300R, A3600R, A3700R, A7000R, A720R, A800R, A810R, A830R, A950RG, CA300-PoE, CP450, CP900, EX1200L, EX200, LR1200, LR350, N350RT, NR1800X, T10, T6, T8, X5000R

</details>

<details>
<summary><b>🏷️ CVE Breakdown by Type (Click to Expand)</b></summary>

| Category | CVEs |
| :--- | :---: |
| Buffer Overflow | 66 |
| Command Injection | 48 |
| Improper Access Controls | 10 |
| Hard-Coded Password | 7 |
| Information Disclosure | 5 |
| **Total** | **136** |

</details>

---

### <img src="https://img.shields.io/badge/D--Link-159%20CVEs-blue?style=for-the-badge" alt="D-Link">

We discovered security issues across **30** different device firmwares from **D-Link**, obtaining a total of **159 CVEs**.

<details>
<summary><b>📡 Affected Product Lines (Click to Expand)</b></summary>

- DCS-932L, DI-7200G, DIR-513, DIR-605L, DIR-618, DIR-619L, DIR-816, DIR-823G, DIR-823Pro, DIR-878, DIR-882, DNR-202L, DNR-322L, DNS-1100-4, DNS-120, DNS-1200-05, DNS-1550-04, DNS-315L, DNS-320, DNS-320L, DNS-320LW, DNS-321, DNS-323, DNS-325, DNS-326, DNS-327L, DNS-340L, DNS-343, DNS-345, DNS-726-4

</details>

<details>
<summary><b>🏷️ CVE Breakdown by Type (Click to Expand)</b></summary>

| Category | CVEs |
| :--- | :---: |
| Buffer Overflow | 81 |
| Improper Access Controls | 62 |
| Command Injection | 44 |
| Information Disclosure | 6 |
| **Total** | **159** |

</details>

---

### <img src="https://img.shields.io/badge/TP--LINK-8%20CVEs-green?style=for-the-badge" alt="TP-LINK">

We discovered security issues across **6** different device firmwares from **TP-LINK**, obtaining a total of **8 CVEs**.

<details>
<summary><b>📡 Affected Product Lines (Click to Expand)</b></summary>

- TL-WR494N, TL-WR740N, TL-WR841N, TL-WR841ND, TL-WR842ND, TL-WR941ND

</details>

<details>
<summary><b>🏷️ CVE Breakdown by Type (Click to Expand)</b></summary>

| Category | CVEs |
| :--- | :---: |
| Buffer Overflow | 10 |
| **Total** | **8** |

</details>

---

### <img src="https://img.shields.io/badge/Linksys-61%20CVEs-purple?style=for-the-badge" alt="Linksys">

We discovered security issues across **8** different device firmwares from **Linksys**, obtaining a total of **61 CVEs**.

<details>
<summary><b>📡 Affected Product Lines (Click to Expand)</b></summary>

- E1700, RE6250, RE6300, RE6350, RE6500, RE7000, RE7000v2, RE9000

</details>

<details>
<summary><b>🏷️ CVE Breakdown by Type (Click to Expand)</b></summary>

| Category | CVEs |
| :--- | :---: |
| Buffer Overflow | 40 |
| Command Injection | 21 |
| Information Disclosure | 1 |
| **Total** | **61** |

</details>

---

### <img src="https://img.shields.io/badge/NETGEAR-63%20CVEs-teal?style=for-the-badge" alt="NETGEAR">

We discovered security issues across **17** different device firmwares from **NETGEAR**, obtaining a total of **63 CVEs**.

<details>
<summary><b>📡 Affected Product Lines (Click to Expand)</b></summary>

- D6400, R6020, R6080, R6120, R6220, R6230, R6260, R6330, R6350, R6400v2, R6700v3, R6850, R6900P, R7000, R7000P, R8500, XR300

</details>

<details>
<summary><b>🏷️ CVE Breakdown by Type (Click to Expand)</b></summary>

| Category | CVEs |
| :--- | :---: |
| Buffer Overflow | 34 |
| Command Injection | 17 |
| **Total** | **63** |

</details>

---

### <img src="https://img.shields.io/badge/Motorola-1%20CVE-yellow?style=for-the-badge" alt="Motorola">

We discovered security issues across **1** different device firmwares from **Motorola**, obtaining a total of **1 CVEs**.

<details>
<summary><b>📡 Affected Product Lines (Click to Expand)</b></summary>

- R6020

</details>

<details>
<summary><b>🏷️ CVE Breakdown by Type (Click to Expand)</b></summary>

| Category | CVEs |
| :--- | :---: |
| Command Injection | 1 |
| **Total** | **1** |

</details>

---

### <img src="https://img.shields.io/badge/Cisco-35%20CVEs-darkblue?style=for-the-badge" alt="Cisco">

We discovered security issues across **4** different device firmwares from **Cisco**, obtaining a total of **35 CVEs**.

<details>
<summary><b>📡 Affected Product Lines (Click to Expand)</b></summary>

- RV110W, RV130, RV130W, RV215W

</details>

<details>
<summary><b>🏷️ CVE Breakdown by Type (Click to Expand)</b></summary>

| Category | CVEs |
| :--- | :---: |
| Buffer Overflow | 35 |
| **Total** | **35** |

</details>

---

### <img src="https://img.shields.io/badge/ARRIS-13%20CVEs-brown?style=for-the-badge" alt="ARRIS">

We discovered security issues across **4** different device firmwares from **ARRIS**, obtaining a total of **13 CVEs**.

<details>
<summary><b>📡 Affected Product Lines (Click to Expand)</b></summary>

- SBR-AC1200P, SBR-AC1900P, SBR-AC3200P, TR3300

</details>

<details>
<summary><b>🏷️ CVE Breakdown by Type (Click to Expand)</b></summary>

| Category | CVEs |
| :--- | :---: |
| Command Injection | 13 |
| **Total** | **13** |

</details>

---

### <img src="https://img.shields.io/badge/Belkin-14%20CVEs-pink?style=for-the-badge" alt="Belkin">

We discovered security issues across **1** different device firmwares from **Belkin**, obtaining a total of **14 CVEs**.

<details>
<summary><b>📡 Affected Product Lines (Click to Expand)</b></summary>

- F9K1015

</details>

<details>
<summary><b>🏷️ CVE Breakdown by Type (Click to Expand)</b></summary>

| Category | CVEs |
| :--- | :---: |
| Buffer Overflow | 11 |
| Command Injection | 3 |
| **Total** | **14** |

</details>

---

## Disclaimer

All vulnerabilities were discovered through responsible research practices. The information provided here is intended for educational and defensive purposes only.

---

## Team

This research was conducted by our security research team through extensive collaborative effort, including firmware analysis, reverse engineering, and vulnerability verification across hundreds of IoT firmwares.
