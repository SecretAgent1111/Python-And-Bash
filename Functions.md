### What is a Function?
 
A function is a reusable block of code. Instead of repeating the same logic, you write it once and call it whenever needed.
 
---
 
### Basic Syntax
 
```python
def function_name():
    # code
```
 
---
 
### Function with Parameters
 
```python
def check_ip(ip):
    print("Checking IP:", ip)
 
check_ip("192.168.1.1")
```
 
---
 
### Return Values
 
Functions can return results instead of just printing them.
 
```python
def detect_bruteforce(attempts):
    if attempts > 10:
        return "Brute force suspected"
 
result = detect_bruteforce(15)
print(result)
```
 
Output:
 
```
Brute force suspected
```
 
Return values allow you to reuse output, integrate with other logic, and build modular detection systems.
 
---
 
### SOC Detection with Functions
 
```python
def detect_bruteforce(attempts):
    if attempts > 10:
        return "ALERT"
    else:
        return "Normal"
 
attempts_list = [3, 8, 15, 20]
 
for attempts in attempts_list:
    result = detect_bruteforce(attempts)
    print("Attempts:", attempts, "| Status:", result)
```
 
Output:
 
```
Attempts: 3  | Status: Normal
Attempts: 8  | Status: Normal
Attempts: 15 | Status: ALERT
Attempts: 20 | Status: ALERT
```
 
---
 
### Advanced SOC Function
 
```python
def analyze_alert(user, ip, attempts):
    if attempts > 10:
        return f"ALERT: Brute force from {ip} (user: {user})"
    else:
        return "Normal activity"
 
print(analyze_alert("admin", "192.168.1.5", 15))
```
 
---
