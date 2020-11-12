# [468](https://leetcode.com/problems/validate-ip-address/). Validate IP Address

Given a string IP, return "IPv4" if IP is a valid IPv4 address, "IPv6" if IP is a valid IPv6 address or "Neither" if IP is not a correct IP of any type.

``` python
# IP  -> IPv4 / IPv6 / Neither
# str -> str 
I: "172.16.254.1"
O: "IPv4"
```

clarification:

* **A valid IPv4** address is an IP in the form "x1.x2.x3.x4" where 
	* **0 <= xi <= 255** and 
	* xi cannot **contain leading zeros**. 
	* For example, "192.168.1.1" and "192.168.1.0" are valid IPv4 addresses but "192.168.01.1", while "192.168.1.00" and "192.168@1.1" are invalid IPv4 addresses.
* **A valid IPv6** address is an IP in the form "x1:x2:x3:x4:x5:x6:x7:x8" where:
	* **1 <= xi.length <= 4**
	* xi is **a hexadecimal string** which may contain digits, lower-case English letter ('a' to 'f') and upper-case English letters ('A' to 'F').
	* Leading zeros are allowed in xi.
* IP consists only of **English letters**, **digits** and the **characters** '.' and ':'.

## Ideas

Simulation:

* Define IPv4 and IPv6 by code

## Exmaple

## Code 

``` python
class Solution:
    def validIPAddress(self, IP: str) -> str:
        if IP.count(".") == 3 and all(self.isIPv4(i) for i in IP.split(".")):
            return "IPv4"
        if IP.count(":") == 7 and all(self.isIPv6(i) for i in IP.split(":")):
            return "IPv6"
        return "Neither"
    
    def isIPv4(self, s):
        try: return str(int(s)) == s and 0 <= int(s) <= 255
        except: return False

    def isIPv6(self, s):
        try: return len(s) <= 4 and int(s, 16) >= 0
        except: return False
```


## Test

```
"172.16.254.1"
"2001:0db8:85a3:0:0:8A2E:0370:7334"
"256.256.256.256"
"2001:0db8:85a3:0:0:8A2E:0370:7334:"
"1e1.4.5.6"
```
