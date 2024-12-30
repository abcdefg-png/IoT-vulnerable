## Overview

- Manufacturer's website information：http://www.dlink.com.cn/
- Firmware download address ：http://www.dlink.com.cn/techsupport/ProductInfo.aspx?m=DIR-816

## Affected version

DIR-816A2 v1.10

## Vulnerability details

An improper access control vulnerability exists in the web management interface of DIR-816A2_FWv1.10CNB05_R1B011D88210. By sending a specially crafted unauthenticated HTTP POST request to the `goform` endpoint with the header set to `form2NetSniper.cgi`, an attacker can set the NetSniper of the device.

## POC

![image-20241230153847480](https://raw.githubusercontent.com/abcdefg-png/images2/main/image-20241230153847480.png)

![image-20241230153858362](https://raw.githubusercontent.com/abcdefg-png/images2/main/image-20241230153858362.png)
