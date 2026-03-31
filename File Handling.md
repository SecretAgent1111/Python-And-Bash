## File Handling
 
In real SOC work, logs are stored in files such as `auth.log`, `syslog`, `firewall.log`, and `windows_event_logs.txt`. Reading and analyzing these files is a core analyst skill.
 
---
 
### Opening a File (Best Practice)
 
```python
with open("auth.log") as file:
    print("File opened")
```
 
Using `with` automatically closes the file and is considered best practice.
 
---
 
### read() vs readlines()
 
`read()` loads the entire file as one block:
 
```python
with open("auth.log") as file:
    data = file.read()
    print(data)
```
 
`readlines()` reads line by line — most commonly used in log analysis:
 
```python
with open("auth.log") as file:
    logs = file.readlines()
```
 
---
 
### Looping Through Logs
 
```python
with open("auth.log") as file:
    logs = file.readlines()
 
for line in logs:
    print(line)
```
 
---
 
### Detecting Failed Logins from a File
 
Given `auth.log`:
 
```
user=admin ip=192.168.1.5 status=failed
user=john ip=10.0.0.2 status=success
user=admin ip=172.16.0.3 status=failed
```
 
Script:
 
```python
with open("auth.log") as file:
    logs = file.readlines()
 
for line in logs:
    if "failed" in line:
        print("ALERT: Failed login detected")
        print(line)
```
 
Output:
 
```
ALERT: Failed login detected
user=admin ip=192.168.1.5 status=failed
 
ALERT: Failed login detected
user=admin ip=172.16.0.3 status=failed
```
 
---
