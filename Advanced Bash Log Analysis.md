# Bash Log Analysis
 
### awk — Field Extraction
 
`awk` extracts a specific column from structured log output.
 
```bash
grep "Failed password" auth.log | awk '{print $11}'
```
 
Given the log format:
 
```
Failed password for admin from 192.168.1.10 port 22 ssh2
```
 
| Field | Value        |
|-------|--------------|
| $1    | Failed       |
| $2    | password     |
| $3    | for          |
| $4    | admin        |
| $5    | from         |
| $6    | 192.168.1.10 |
 
Note: The IP field position varies depending on the log format. Always verify the field number before using in production.
 
---
 
### Full Pipeline — Find Top Attackers
 
```bash
grep "Failed password" auth.log | awk '{print $11}' | sort | uniq -c | sort -nr
```
 
Output:
 
```
20 192.168.1.10
 8 172.16.0.3
 3 10.0.0.5
```
 
192.168.1.10 made 20 attempts — likely a brute force source.
 
---
 
### Step-by-Step Breakdown
 
```bash
# Step 1 — Filter failed logins
grep "Failed password" auth.log
 
# Step 2 — Extract IP addresses
awk '{print $11}'
 
# Step 3 — Sort alphabetically
sort
 
# Step 4 — Count duplicates
uniq -c
 
# Step 5 — Sort by frequency (highest first)
sort -nr
```
 
---
