### What is Python in SOC?
 
SOC analysts use Python to automate repetitive tasks including log parsing, alert automation, threat intel scripts, API queries (VirusTotal, AbuseIPDB), and data analysis.
 
Instead of manually reviewing 1000 failed logins, Python can automatically filter and flag them.
 
---
 
### Variables
 
A variable stores data and acts like a label.
 
```python
ip = "192.168.1.10"
status = "failed"
```
 
| Variable | Value        |
|----------|--------------|
| ip       | 192.168.1.10 |
| status   | failed       |
 
---
 
### Strings
 
A string is text data, always enclosed in quotes.
 
```python
username = "admin"
status = "failed"
```
 
SOC examples: `"admin"`, `"failed"`, `"login attempt"`
 
---
 
### Integers
 
An integer is a whole number.
 
```python
attempts = 5
port = 22
```
 
| Integer | Meaning        |
|---------|----------------|
| 22      | SSH port       |
| 443     | HTTPS port     |
| 5       | Login attempts |
 
---
 
### print() Function
 
`print()` displays output on the screen.
 
```python
ip = "192.168.1.10"
print("Source IP:", ip)
```
 
Output:
 
```
Source IP: 192.168.1.10
```
 
---
 
### Full SOC Example
 
```python
ip = "192.168.1.10"
username = "admin"
status = "failed"
 
print("Login Attempt Detected")
print("Username:", username)
print("Source IP:", ip)
print("Result:", status)
```
 
Output:
 
```
Login Attempt Detected
Username: admin
Source IP: 192.168.1.10
Result: failed
```
 
---
 
### Practice Lab — soc_python_basics.py
 
```python
# SOC Python Basics
 
username = "admin"
ip = "192.168.1.50"
login_result = "failed"
 
print("SOC Login Alert")
print("Username:", username)
print("Source IP:", ip)
print("Login Result:", login_result)
```
 
Expected output:
 
```
SOC Login Alert
Username: admin
Source IP: 192.168.1.50
Login Result: failed
```
 
---
