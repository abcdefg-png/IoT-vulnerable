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
<h1>132</h1>
<b>📡 Device Firmwares</b>
<br><br>
</td>
<td align="center" width="200">
<br>
<h1>897</h1>
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

- **FalconScope: Effective and Efficient Detection of Hidden Web Interfaces in IoT Devices**
  *WWW 2026* | **CCF-A**

- **Bridge: High-Order Taint Vulnerabilities Detection in Linux-based IoT Firmware**
  *IEEE S&P 2026* | **CCF-A**

- **Bond: Constraint-Directed Fuzzing for Automated Validation of Taint Analysis  Results in Linux-based IoT Firmware**
  *USENIX Security 2026* | **CCF-A**

- **LoopSCC: Summarizing Complex Multi-branch Nested Loops via Periodic Oscillation Interval**
  *ICSE 2026* | **CCF-A**

- **FirmSV: Detecting Stored Vulnerabilities in IoT Firmware using Static Taint Analysis**
  *CSCWD 2026* | CCF-C

<sub>*Papers under submission: ISSTA, TSE*</sub>

## Summary by Vendor

<table>
<tr><th align="center">Vendor</th><th align="center">Affected Firmwares</th><th align="center">CVEs Assigned</th></tr>
<tr><td align="center"><b>Tenda</b></td><td align="center">37</td><td align="center">416</td></tr>
<tr><td align="center"><b>TOTOLINK</b></td><td align="center">25</td><td align="center">136</td></tr>
<tr><td align="center"><b>D-Link</b></td><td align="center">29</td><td align="center">150</td></tr>
<tr><td align="center"><b>TP-LINK</b></td><td align="center">6</td><td align="center">8</td></tr>
<tr><td align="center"><b>Linksys</b></td><td align="center">8</td><td align="center">61</td></tr>
<tr><td align="center"><b>NETGEAR</b></td><td align="center">17</td><td align="center">63</td></tr>
<tr><td align="center"><b>Motorola</b></td><td align="center">1</td><td align="center">1</td></tr>
<tr><td align="center"><b>Cisco</b></td><td align="center">4</td><td align="center">35</td></tr>
<tr><td align="center"><b>ARRIS</b></td><td align="center">4</td><td align="center">13</td></tr>
<tr><td align="center"><b>Belkin</b></td><td align="center">1</td><td align="center">14</td></tr>
<tr><td align="center"><b>Total</b></td><td align="center"><b>132</b></td><td align="center"><b>897</b></td></tr>
<tr bgcolor="#f3e8ff"><td align="center"><b>Matter Protocol</b></td><td align="center">10 vendors</td><td align="center">confirmed by vendor</td></tr>
</table>

---

## Vulnerability Type Distribution

<table>
<tr><th align="left">Vulnerability Type</th><th align="left">Description</th></tr>
<tr><td>💥 <b>Buffer Overflow</b></td><td>The most prevalent type, accounting for the majority of all findings</td></tr>
<tr><td>💉 <b>Command Injection</b></td><td>Remote command execution through improperly sanitized inputs</td></tr>
<tr><td>🔓 <b>Improper Access Controls</b></td><td>Unauthorized access to restricted functionalities</td></tr>
<tr><td>📂 <b>Information Disclosure</b></td><td>Exposure of sensitive device or configuration data</td></tr>
<tr><td>🔑 <b>Hard-Coded Password</b></td><td>Embedded credentials in firmware</td></tr>
<tr><td>🔄 <b>CSRF</b></td><td>Cross-Site Request Forgery enabling unauthorized actions</td></tr>
<tr bgcolor="#f3e8ff"><td>🧩 <b>UMCCI Flaws</b></td><td>Unauthorized Matter Cluster Command Injection flaws in Matter protocol implementations</td></tr>
</table>

---

## Detailed Findings by Vendor

### <img src="https://img.shields.io/badge/Matter%20Protocol-10%20Vendors-blueviolet?style=for-the-badge" alt="Matter Protocol">

We identified **UMCCI (Unauthorized Matter Cluster Command Injection)** flaws across **10** vendors' Matter protocol implementations. All findings have been **confirmed by the respective vendors**.

<details>
<summary><b>📡 Affected Vendors (Click to Expand)</b></summary>

- Apple
- Google
- Samsung
- Xiaomi
- Amazon
- Tuya
- uHome+
- Aqara
- WiZ
- Vivo

</details>

---

### <img src="https://img.shields.io/badge/Tenda-416%20CVEs-red?style=for-the-badge" alt="Tenda">

We discovered security issues across **37** different device firmwares from **Tenda**, obtaining a total of **416 CVEs**.

<details>
<summary><b>📡 Affected Product Lines (Click to Expand)</b></summary>

- 4G300, A18, AC10Uv1.0, AC10v4.0, AC15, AC18, AC23, AC5, AC500, AC6, AC7V1.0, AC8v4, AC9, AX12, AX1803, AX1806, AX3, F1202, F1203, FH1201, FH1202, FH1203, FH1205, FH1206, G1, G3, O1, O3V2.0, O5V1.0, O6, TX9, W15EV1.0, W20EV4.0, W30Ev1.0, W9, i21, i22

</details>

<details>
<summary><b>🏷️ CVE Breakdown by Type (Click to Expand)</b></summary>

| Category | CVEs |
| :--- | :---: |
| Buffer Overflow | 365 |
| Command Injection | 36 |
| Improper Access Controls | 10 |
| CSRF | 5 |
| Information Disclosure | 2 |
| **Total** | **416** |

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

### <img src="https://img.shields.io/badge/D--Link-150%20CVEs-blue?style=for-the-badge" alt="D-Link">

We discovered security issues across **29** different device firmwares from **D-Link**, obtaining a total of **150 CVEs**.

<details>
<summary><b>📡 Affected Product Lines (Click to Expand)</b></summary>

- DCS-932L, DI-7200G, DIR-605L, DIR-618, DIR-619L, DIR-816, DIR-823G, DIR-823Pro, DIR-878, DIR-882, DNR-202L, DNR-322L, DNS-1100-4, DNS-120, DNS-1200-05, DNS-1550-04, DNS-315L, DNS-320, DNS-320L, DNS-320LW, DNS-321, DNS-323, DNS-325, DNS-326, DNS-327L, DNS-340L, DNS-343, DNS-345, DNS-726-4

</details>

<details>
<summary><b>🏷️ CVE Breakdown by Type (Click to Expand)</b></summary>

| Category | CVEs |
| :--- | :---: |
| Buffer Overflow | 72 |
| Improper Access Controls | 62 |
| Command Injection | 44 |
| Information Disclosure | 6 |
| **Total** | **150** |

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
