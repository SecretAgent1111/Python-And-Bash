Conditions
 
### What are Conditions?
 
Conditions are decision-making logic in code. In SOC terms: if something suspicious happens, raise an alert; otherwise, ignore it.
 
---
 
### if Statement
 
Runs when the condition is true.
 
```python
attempts = 15
 
if attempts > 10:
    print("Possible brute force attack")
```
 
---
 
### else Statement
 
Runs when the condition is false.
 
```python
attempts = 5
 
if attempts > 10:
    print("Attack")
else:
    print("Normal activity")
```
 
---
 
### elif — Multiple Conditions
 
Used to check multiple conditions in sequence.
 
```python
attempts = 10
 
if attempts > 15:
    print("High risk attack")
elif attempts > 5:
    print("Suspicious activity")
else:
    print("Normal")
```
 
---
 
### Detection Logic (SOC Context)
 
This mirrors how SIEM rules work internally.
 
| Condition          | Meaning            |
|--------------------|--------------------|
| attempts > 10      | Brute force        |
| attempts 5 to 10   | Suspicious         |
| attempts < 5       | Normal             |
 
---
 
### Full SOC Example
 
```python
username = "admin"
ip = "192.168.1.10"
attempts = 12
 
if attempts > 10:
    print("ALERT: Brute Force Attack Detected")
    print("Username:", username)
    print("IP:", ip)
elif attempts > 5:
    print("Warning: Suspicious Login Attempts")
else:
    print("Normal Activity")
```
 
Output:
 
```
ALERT: Brute Force Attack Detected
Username: admin
IP: 192.168.1.10
```
 
---
