# SOC Automation Project
 
### Project: SOC Log Analyzer
 
A mini SOC detection tool that reads log files, extracts IP addresses, counts failed login attempts, detects brute force attacks, and generates alerts. This is the core logic behind a basic SIEM detection rule.
 
---
 
### Project Flow
 
```
1. Read log file
2. Filter failed logins
3. Extract IP addresses using regex
4. Count attempts per IP
5. Detect brute force (more than 10 attempts)
6. Print alert report
```
 
---
 
### Example Log — auth.log
 
```
Failed password for admin from 192.168.1.10
Failed password for admin from 192.168.1.10
Failed password for root from 172.16.0.3
```
 
---
 
### Full Project Code — soc_log_analyzer.py
 
```python
# SOC Log Analyzer - Final Project
 
import re
 
log_file = "auth.log"
 
ip_counts = {}
 
# Step 1: Read log file
with open(log_file) as file:
    for line in file:
 
        # Step 2: Filter failed logins
        if "Failed password" in line:
 
            # Step 3: Extract IP using regex
            ip_match = re.findall(r"\d+\.\d+\.\d+\.\d+", line)
 
            if ip_match:
                ip = ip_match[0]
 
                # Step 4: Count attempts per IP
                if ip in ip_counts:
                    ip_counts[ip] += 1
                else:
                    ip_counts[ip] = 1
 
# Step 5: Detect brute force and generate report
print("=== SOC ALERT REPORT ===")
 
for ip, count in ip_counts.items():
    print(f"{ip} -> {count} attempts")
 
    if count > 10:
        print("ALERT: Brute Force Detected!")
 
    print("----------------------------")
```
 
---
 
### Expected Output
 
```
=== SOC ALERT REPORT ===
192.168.1.10 -> 12 attempts
ALERT: Brute Force Detected!
----------------------------
172.16.0.3 -> 3 attempts
----------------------------
```
 
---
