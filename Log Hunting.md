# Log Hunting Commands
 
 During incidents, you run one command and get the answer immediately. No manual reading required.
 
---
 
### grep — Search Logs
 
```bash
grep "Failed password" auth.log
```
 
Filters and returns only matching lines.
 
Output:
 
```
Failed password for admin from 192.168.1.10
Failed password for root from 172.16.0.3
```
 
---
 
### wc -l — Count Lines
 
```bash
grep "Failed password" auth.log | wc -l
```
 
Counts the number of matching lines.
 
Output:
 
```
25
```
 
---
 
### cut — Extract Specific Fields
 
```bash
grep "Failed password" auth.log | cut -d " " -f 9
```
 
Extracts a specific column from each line (such as an IP address).
 
Output:
 
```
192.168.1.10
172.16.0.3
```
 
---
 
### Find Top Attacker IPs
 
```bash
grep "Failed password" auth.log | cut -d " " -f 9 | sort | uniq -c | sort -nr
```
 
Output:
 
```
15 192.168.1.10
 5 172.16.0.3
```
 
192.168.1.10 attempted 15 times — likely a brute force attack.
 
---
 
### Full Attack Investigation Workflow
 
```bash
# Step 1 — Find failed logins
grep "Failed password" auth.log
 
# Step 2 — Count total attempts
grep "Failed password" auth.log | wc -l
 
# Step 3 — Extract attacker IPs
grep "Failed password" auth.log | cut -d " " -f 9
 
# Step 4 — Rank by frequency
grep "Failed password" auth.log | cut -d " " -f 9 | sort | uniq -c | sort -nr
```
 
---
