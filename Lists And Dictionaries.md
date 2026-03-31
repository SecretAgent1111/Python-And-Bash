 ### Lists And Dictionaries
 
Real logs in tools like Splunk, Microsoft Sentinel, and QRadar are structured data, not simple variables. They arrive in JSON-like format:
 
```json
{
  "user": "admin",
  "ip": "192.168.1.5",
  "event": "failed_login"
}
```
 
This is exactly what a Python dictionary represents.
 
---
 
### Lists
 
A list stores multiple values.
 
```python
ips = ["192.168.1.1", "10.0.0.5", "172.16.0.3"]
 
for ip in ips:
    print(ip)
```
 
In SOC terms, a list holds multiple alerts, logs, or IP addresses.
 
---
 
### Dictionaries
 
A dictionary stores data as key-value pairs.
 
```python
alert = {
    "user": "admin",
    "ip": "192.168.1.5",
    "event": "failed_login"
}
 
print(alert["ip"])
```
 
Output:
 
```
192.168.1.5
```
 
| Key   | Value        |
|-------|--------------|
| user  | admin        |
| ip    | 192.168.1.5  |
| event | failed_login |
 
---
 
### Combining Lists and Dictionaries
 
```python
alerts = [
    {"user": "admin", "ip": "192.168.1.5", "event": "failed_login"},
    {"user": "john",  "ip": "10.0.0.2",   "event": "success_login"},
    {"user": "admin", "ip": "172.16.0.3",  "event": "failed_login"}
]
 
for alert in alerts:
    if alert["event"] == "failed_login":
        print("ALERT: Failed login detected")
        print("User:", alert["user"])
        print("IP:", alert["ip"])
        print("-------------------")
```
 
---
