### What is a Loop?
 
A loop repeats a task multiple times. In SOC terms, instead of manually checking one alert, you process thousands automatically. This is how SIEM and detection scripts handle logs.
 
---
 
### for Loop
 
Iterates through a list one item at a time.
 
```python
ips = ["10.0.0.1", "192.168.1.1", "172.16.1.5"]
 
for ip in ips:
    print("Investigating:", ip)
```
 
Output:
 
```
Investigating: 10.0.0.1
Investigating: 192.168.1.1
Investigating: 172.16.1.5
```
 
---
 
### while Loop
 
Runs until a condition becomes false.
 
```python
attempts = 1
 
while attempts <= 3:
    print("Checking attempt:", attempts)
    attempts += 1
```
 
Output:
 
```
Checking attempt: 1
Checking attempt: 2
Checking attempt: 3
```
 
---
 
### Loops with Detection Logic
 
```python
ips = ["192.168.1.10", "10.0.0.5", "192.168.1.20"]
 
for ip in ips:
    if ip.startswith("192.168"):
        print("Internal IP:", ip)
    else:
        print("External IP - Investigate:", ip)
```
 
Output:
 
```
Internal IP: 192.168.1.10
External IP - Investigate: 10.0.0.5
Internal IP: 192.168.1.20
```
 
---
 
### Brute Force Simulation
 
```python
attempts_list = [2, 5, 12, 1, 20]
 
for attempts in attempts_list:
    if attempts > 10:
        print("ALERT: Brute force detected ->", attempts)
    else:
        print("Normal activity ->", attempts)
```
 
---
 
