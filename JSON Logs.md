### What is JSON?
 
JSON (JavaScript Object Notation) is structured data stored as key-value pairs. It looks exactly like a Python dictionary. Real SIEM tools — Splunk, Microsoft Sentinel, Elastic — deliver logs in this format.
 
```json
{
  "timestamp": "2026-03-24 10:00:00",
  "user": "admin",
  "ip": "192.168.1.5",
  "event": "login_failed"
}
```
 
---
 
### Convert JSON to Python
 
```python
import json
 
data = '{"ip":"192.168.1.5"}'
 
log = json.loads(data)
 
print(log["ip"])
```
 
Output:
 
```
192.168.1.5
```
 
| Step           | Meaning                             |
|----------------|-------------------------------------|
| `json.loads()` | Converts JSON string to Python dict |
| `log["ip"]`    | Accesses value by key               |
 
---
 
### Detection Logic on JSON Log
 
```python
import json
 
data = '{"user":"admin","ip":"192.168.1.5","event":"login_failed"}'
 
log = json.loads(data)
 
if log["event"] == "login_failed":
    print("ALERT: Failed login detected")
    print("User:", log["user"])
    print("IP:", log["ip"])
```
 
---
 
### Processing Multiple JSON Logs
 
```python
import json
 
logs = [
    '{"user":"admin","ip":"192.168.1.5","event":"login_failed"}',
    '{"user":"john","ip":"10.0.0.2","event":"login_success"}',
    '{"user":"admin","ip":"172.16.0.3","event":"login_failed"}'
]
 
for entry in logs:
    log = json.loads(entry)
 
    if log["event"] == "login_failed":
        print("ALERT:", log["ip"])
```
 
Output:
 
```
ALERT: 192.168.1.5
ALERT: 172.16.0.3
```
 
---
