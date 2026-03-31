### What is Regex?
 
Regex (Regular Expressions) is pattern matching. Instead of reading logs manually, you define a pattern and Python finds everything that matches — IPs, domains, hashes, emails, and more.
 
---
 
### Import the Module
 
```python
import re
```
 
---
 
### Extract an IP Address
 
```python
import re
 
log = "Failed login from 192.168.1.5"
 
ip = re.findall(r"\d+\.\d+\.\d+\.\d+", log)
 
print(ip)
```
 
Output:
 
```
['192.168.1.5']
```
 
Pattern breakdown:
 
| Part  | Meaning       |
|-------|---------------|
| `\d+` | One or more digits |
| `\.`  | A literal dot |
 
Combined, `\d+\.\d+\.\d+\.\d+` matches any IPv4 address.
 
---
 
### Extract Multiple Indicators
 
```python
import re
 
log = "Connection from 192.168.1.5 to malicious.com"
 
ips     = re.findall(r"\d+\.\d+\.\d+\.\d+", log)
domains = re.findall(r"[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}", log)
 
print("IP:", ips)
print("Domain:", domains)
```
 
Output:
 
```
IP: ['192.168.1.5']
Domain: ['malicious.com']
```
 
---
 
### Processing Multiple Logs
 
```python
import re
 
logs = [
    "Failed login from 192.168.1.5",
    "Connection to badsite.com from 10.0.0.2",
    "Malware hash detected: a3f5d8c9e1b2"
]
 
for log in logs:
    ip     = re.findall(r"\d+\.\d+\.\d+\.\d+", log)
    domain = re.findall(r"[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}", log)
 
    if ip:
        print("IP Found:", ip)
 
    if domain:
        print("Domain Found:", domain)
 
    print("------------------")
```
 
---
 
