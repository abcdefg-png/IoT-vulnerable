## Overview

- Manufacturer's website information：http://www.dlink.com.cn/
- Firmware download address ：http://www.dlink.com.cn/techsupport/ProductInfo.aspx?m=DIR-816

## Affected version

DIR-816A2 v1.10

## Vulnerability details

An information disclosure vulnerability exists in the web management interface of DIR-816A2_FWv1.10CNB05_R1B011D88210. By sending a specially crafted unauthenticated HTTP POST request to the `d_status.asp`, an attacker can retrieve sensitive device information.

## POC

![image-20241230152922020](https://raw.githubusercontent.com/abcdefg-png/images2/main/image-20241230152922020.png)

![image-20241230153040612](https://raw.githubusercontent.com/abcdefg-png/images2/main/image-20241230153040612.png)
