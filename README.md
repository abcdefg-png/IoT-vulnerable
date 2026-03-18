# IoT Vulnerability Research Report

## Overview

Our research team has conducted an extensive security analysis on IoT devices from multiple vendors. Through systematic vulnerability discovery and responsible disclosure, we have identified a large number of security issues and obtained **CVE** identifiers for the vast majority of them.

<div align="center">
<table>
<tr>
<td align="center" width="200">
<br>
<h1>5</h1>
<b>🏭 Vendors Affected</b>
<br><br>
</td>
<td align="center" width="200">
<br>
<h1>64</h1>
<b>📡 Device Firmwares</b>
<br><br>
</td>
<td align="center" width="200">
<br>
<h1>516</h1>
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
  *NDSS 2026* | CCF-A

- **FalconScope: Effective and Efficient Detection of Hidden Web Interfaces in IoT Devices**
  *WWW 2026* | CCF-A

- **FirmSV: Detecting Stored Vulnerabilities in IoT Firmware using Static Taint Analysis**
  *CSCWD 2026* | CCF-C

## Summary by Vendor

| Vendor | Affected Firmwares | CVEs Assigned |
| :---: | :---: | :---: |
| **Tenda** | 37 | 350 |
| **TOTOLINK** | 17 | 94 |
| **D-Link** | 6 | 69 |
| **TP-LINK** | 3 | 3 |
| **Linksys** | 1 | 0 |
| **Total** | **64** | **516** |

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

---

## Detailed Findings by Vendor

### <img src="https://img.shields.io/badge/Tenda-350%20CVEs-red?style=for-the-badge" alt="Tenda">

We discovered security issues across **37** different device firmwares from **Tenda**, obtaining a total of **350 CVEs**.

<details>
<summary><b>📡 Affected Product Lines (Click to Expand)</b></summary>

- **A Series**: A18, AC5, AC6, AC7, AC8v4, AC9, AC10v4, AC10U, AC15, AC18, AC23, AC500
- **AX Series**: AX1803, AX1806
- **F Series**: F1202, F1203, FH1201, FH1202, FH1203, FH1205, FH1206
- **W Series**: W9, W15E, W20E, W30E
- **TX Series**: TX9
- **G Series**: G3, 4G300
- **i Series**: i21, i22
- **O Series**: O1, O3, O5, O6

</details>

<details>
<summary><b>🏷️ CVE Breakdown by Type (Click to Expand)</b></summary>

| Category | CVEs |
| :--- | :---: |
| Buffer Overflow | ~290 |
| Command Injection | ~20 |
| Improper Access Controls | ~24 |
| CSRF | 6 |
| Information Disclosure | ~10 |
| **Total** | **350** |

</details>

---

### <img src="https://img.shields.io/badge/TOTOLINK-93%20CVEs-orange?style=for-the-badge" alt="TOTOLINK">

We discovered security issues across **17** different device firmwares from **TOTOLINK**, obtaining a total of **93 CVEs**.

<details>
<summary><b>📡 Affected Product Lines (Click to Expand)</b></summary>

- **A Series**: A3000RU, A3100R, A3300R, A3600R, A3700R, A7000R
- **CA Series**: CA300-PoE
- **CP Series**: CP450, CP900
- **EX Series**: EX200, EX1200L
- **LR Series**: LR350, LR1200
- **NR Series**: NR1800X
- **N Series**: N350RT
- **AC Series**: AC1200 T8, AC1200 T10

</details>

<details>
<summary><b>🏷️ CVE Breakdown by Type (Click to Expand)</b></summary>

| Category | CVEs |
| :--- | :---: |
| Buffer Overflow | ~53 |
| Command Injection | ~11 |
| Improper Access Controls | 9 |
| Hard-Coded Password | 7 |
| Information Disclosure | ~14 |
| **Total** | **94** |

</details>

---

### <img src="https://img.shields.io/badge/D--Link-69%20CVEs-blue?style=for-the-badge" alt="D-Link">

We discovered security issues across **6** different device firmwares from **D-Link**, obtaining a total of **69 CVEs**.

<details>
<summary><b>📡 Affected Product Lines (Click to Expand)</b></summary>

- **DIR Series**: DIR-605L, DIR-618, DIR-619L, DIR-816, DIR-823G, DIR-878

</details>

<details>
<summary><b>🏷️ CVE Breakdown by Type (Click to Expand)</b></summary>

| Category | CVEs |
| :--- | :---: |
| Buffer Overflow | ~41 |
| Improper Access Controls | ~25 |
| Information Disclosure | ~3 |
| **Total** | **69** |

</details>

---

### <img src="https://img.shields.io/badge/TP--LINK-3%20CVEs-green?style=for-the-badge" alt="TP-LINK">

We discovered security issues across **3** different device firmwares from **TP-LINK**, obtaining a total of **3 CVEs**.

<details>
<summary><b>📡 Affected Product Lines (Click to Expand)</b></summary>

- TL-WR841ND v11
- TL-WR941ND v6
- TL-WR740N v6

</details>

<details>
<summary><b>🏷️ CVE Breakdown by Type (Click to Expand)</b></summary>

| Category | CVEs |
| :--- | :---: |
| Buffer Overflow | 3 |
| **Total** | **3** |

</details>

---

### <img src="https://img.shields.io/badge/Linksys-0%20CVE-lightgrey?style=for-the-badge" alt="Linksys">

We discovered a security issue in **1** device firmware from **Linksys**, obtaining **0 CVE**.

<details>
<summary><b>📡 Affected Product Lines (Click to Expand)</b></summary>

- RE7000v2

</details>

<details>
<summary><b>🏷️ CVE Breakdown by Type (Click to Expand)</b></summary>

| Category | CVEs |
| :--- | :---: |
| Information Disclosure | 0 |
| **Total** | **0** |

</details>

---

## Disclaimer

All vulnerabilities were discovered through responsible research practices. The information provided here is intended for educational and defensive purposes only.

---

## Team

This research was conducted by our security research team through extensive collaborative effort, including firmware analysis, reverse engineering, and vulnerability verification across hundreds of IoT firmwares.
