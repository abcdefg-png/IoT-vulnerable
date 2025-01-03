## Overview

- Manufacturer's website information：https://support.linksys.com/
- Firmware download address ：https://downloads.linksys.com/support/assets/firmware/RE7000v2_PROD_FW_v2.0.15_211230_1012.bin

## Affected version

RE7000v2_PROD_FW_v2.0.15_211230_1012

## Vulnerability details

In Linksys RE7000v2_PROD_FW_v2.0.15_211230_1012, an attacker can obtain the configuration information without authorization through `SysInfo.htm`. When making a request to `SysInfo.htm`, the attacker can obtain the configuration information without authorization.

## POC

![image-20241214220742694](https://raw.githubusercontent.com/abcdefg-png/images2/main/image-20241214220742694.png)
