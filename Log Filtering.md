### What is Log Filtering?
 
Log filtering means finding specific patterns inside logs. Out of thousands of log lines, you extract only the suspicious ones — failed logins, errors, or attack patterns.
 
---
 
### Example Log Format
 
```
Failed password for admin from 192.168.1.10
Accepted password for john from 10.0.0.5
Failed password for root from 172.16.0.3
```
 
---
 
### Basic Filtering
 
```python
with open("auth.log") as file:
    for line in file:
        if "Failed" in line:
            print(line)
```
 
This logic is identical to how Splunk queries, KQL filters, and SIEM detection rules operate.
 
---
 
### Clean Output
 
```python
with open("auth.log") as file:
    for line in file:
        if "Failed" in line:
            print("ALERT:", line.strip())
```
 
---
 
### Extract User and IP from Log Line
 
```python
with open("auth.log") as file:
    for line in file:
        if "Failed" in line:
            parts = line.split()
 
            user = parts[3]
            ip   = parts[-1]
 
            print("ALERT: Failed Login")
            print("User:", user)
            print("IP:", ip)
            print("-------------------")
```
 
Expected output:
 
```
ALERT: Failed Login
User: admin
IP: 192.168.1.10
-------------------
ALERT: Failed Login
User: root
IP: 172.16.0.3
-------------------
```
 
---
 
