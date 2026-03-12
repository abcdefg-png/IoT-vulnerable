# 🔒 IoT Vulnerability Research Report

## 📋 Overview

Our research team has conducted an extensive security analysis across IoT devices from multiple vendors. Through systematic vulnerability discovery and responsible disclosure, we have achieved significant results in improving IoT security.

<table>
  <tr>
    <th>📊 Metric</th>
    <th>Count</th>
  </tr>
  <tr>
    <td>🏭 Vendors Affected</td>
    <td><b>5</b></td>
  </tr>
  <tr>
    <td>📡 Device Models Affected</td>
    <td><b>76</b></td>
  </tr>
  <tr>
    <td>🐛 Vulnerabilities Discovered</td>
    <td><b>526</b></td>
  </tr>
  <tr>
    <td>🏷️ CVEs Assigned</td>
    <td><b>516</b></td>
  </tr>
</table>

---

## 📈 Summary by Vendor

| Vendor | Affected Models | Vulnerabilities | CVEs Assigned |
| :---: | :---: | :---: | :---: |
| **Tenda** | 40 | 352 | 350 |
| **TOTOLINK** | 26 | 93 | 93 |
| **D-Link** | 6 | 77 | 69 |
| **TP-LINK** | 3 | 3 | 3 |
| **Linksys** | 1 | 1 | 0 |
| **Total** | **76** | **526** | **516** |

---

## 🔍 Vulnerability Type Distribution

| Vulnerability Type | Description |
| :--- | :--- |
| 💥 **Buffer Overflow** | The most prevalent type, accounting for the majority of all findings |
| 💉 **Command Injection** | Remote command execution through improperly sanitized inputs |
| 🔓 **Improper Access Controls** | Unauthorized access to restricted functionalities |
| 📂 **Information Disclosure** | Exposure of sensitive device or configuration data |
| 🔑 **Hard-Coded Password** | Embedded credentials in firmware |
| 🔄 **CSRF** | Cross-Site Request Forgery enabling unauthorized actions |

---

## 🏭 Detailed Findings by Vendor

### <img src="https://img.shields.io/badge/Tenda-352%20Vulnerabilities-red?style=for-the-badge" alt="Tenda">

We discovered vulnerabilities across **40** different device models from **Tenda**, revealing a total of **352 vulnerabilities** and obtaining **350 CVEs**.

<details>
<summary><b>📡 Affected Product Lines (Click to Expand)</b></summary>

- **A Series**: A18, AC5, AC6, AC7, AC8v4, AC9, AC10v4, AC10U, AC15, AC18, AC23, AC500
- **AX Series**: AX1803, AX1806
- **F Series**: F1202, F1203, FH1201, FH1202, FH1203, FH1205, FH1206
- **W Series**: W9, W15E, W20E, W30E
- **TX Series**: TX9
- **G Series**: G3
- **4G Series**: 4G300
- **i Series**: i21, i22
- **O Series**: O1, O3, O5, O6

</details>

<details>
<summary><b>🐛 Vulnerability Breakdown (Click to Expand)</b></summary>

| Category | Vulnerabilities | CVEs |
| :--- | :---: | :---: |
| Buffer Overflow | ~290 | ~290 |
| Command Injection | ~20 | ~20 |
| Improper Access Controls | 10 | 10 |
| CSRF | 6 | 6 |
| Information Disclosure | 2 | 0 |
| **Total** | **352** | **350** |

</details>

---

### <img src="https://img.shields.io/badge/TOTOLINK-93%20Vulnerabilities-orange?style=for-the-badge" alt="TOTOLINK">

We discovered vulnerabilities across **26** different device models from **TOTOLINK**, revealing a total of **93 vulnerabilities** and obtaining **93 CVEs**.

<details>
<summary><b>📡 Affected Product Lines (Click to Expand)</b></summary>

- **A Series**: A3100R, A3300R, A3600R, A3700R, A7000R
- **CA Series**: CA300-PoE
- **CP Series**: CP450, CP900
- **EX Series**: EX200, EX1200L
- **LR Series**: LR350, LR1200
- **NR Series**: NR1800X
- **N Series**: N350RT
- **AC Series**: AC1200 T8, AC1200 T10

</details>

<details>
<summary><b>🐛 Vulnerability Breakdown (Click to Expand)</b></summary>

| Category | Vulnerabilities | CVEs |
| :--- | :---: | :---: |
| Buffer Overflow | ~52 | ~52 |
| Command Injection | ~11 | ~11 |
| Improper Access Controls | 9 | 9 |
| Hard-Coded Password | 7 | 7 |
| Information Disclosure | 5 | 5 |
| **Total** | **93** | **93** |

</details>

---

### <img src="https://img.shields.io/badge/D--Link-77%20Vulnerabilities-blue?style=for-the-badge" alt="D-Link">

We discovered vulnerabilities across **6** different device models from **D-Link**, revealing a total of **77 vulnerabilities** and obtaining **69 CVEs**.

<details>
<summary><b>📡 Affected Product Lines (Click to Expand)</b></summary>

- **DIR Series**: DIR-605L, DIR-618, DIR-619L, DIR-816, DIR-823G, DIR-878

</details>

<details>
<summary><b>🐛 Vulnerability Breakdown (Click to Expand)</b></summary>

| Category | Vulnerabilities | CVEs |
| :--- | :---: | :---: |
| Buffer Overflow | ~41 | ~41 |
| Improper Access Controls | ~33 | ~25 |
| Information Disclosure | ~3 | ~1 |
| **Total** | **77** | **69** |

</details>

---

### <img src="https://img.shields.io/badge/TP--LINK-3%20Vulnerabilities-green?style=for-the-badge" alt="TP-LINK">

We discovered vulnerabilities across **3** different device models from **TP-LINK**, revealing a total of **3 vulnerabilities** and obtaining **3 CVEs**.

<details>
<summary><b>📡 Affected Product Lines (Click to Expand)</b></summary>

- TL-WR841ND v11
- TL-WR941ND v6
- TL-WR740N V6

</details>

<details>
<summary><b>🐛 Vulnerability Breakdown (Click to Expand)</b></summary>

| Category | Vulnerabilities | CVEs |
| :--- | :---: | :---: |
| Buffer Overflow | 3 | 3 |
| **Total** | **3** | **3** |

</details>

---

### <img src="https://img.shields.io/badge/Linksys-1%20Vulnerability-lightgrey?style=for-the-badge" alt="Linksys">

We discovered vulnerabilities in **1** device model from **Linksys**, revealing **1 vulnerability**.

<details>
<summary><b>📡 Affected Product Lines (Click to Expand)</b></summary>

- RE7000v2

</details>

<details>
<summary><b>🐛 Vulnerability Breakdown (Click to Expand)</b></summary>

| Category | Vulnerabilities | CVEs |
| :--- | :---: | :---: |
| Information Disclosure | 1 | 0 |
| **Total** | **1** | **0** |

</details>

---

## ⚠️ Disclaimer

All vulnerabilities were discovered through responsible research practices. We have followed responsible disclosure procedures and reported all findings to the respective vendors prior to public disclosure. The information provided here is intended for educational and defensive purposes only.

---

## 👥 Team

This research was conducted by our security research team through extensive collaborative effort, including firmware analysis, reverse engineering, and vulnerability verification across hundreds of IoT devices.
