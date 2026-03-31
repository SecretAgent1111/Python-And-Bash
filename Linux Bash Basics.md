# Linux Bash Basics
 
### Why Linux Matters in SOC
 
Logs on real servers are stored on Linux systems. Analysts use the terminal to investigate quickly without opening a GUI. Key log locations include `/var/log/auth.log`, `/var/log/syslog`, and `/var/log/apache2/access.log`.
 
---
 
### ls — List Files
 
```bash
ls
```
 
Shows files in the current directory. Used to locate log files quickly.
 
---
 
### cd — Change Directory
 
```bash
cd /var/log
cd ..
```
 
Navigate to log directories or move back up the directory tree.
 
---
 
### cat — View File Contents
 
```bash
cat auth.log
```
 
Displays the entire file. Not ideal for large files due to overwhelming output.
 
---
 
### less — Scroll Through Logs
 
```bash
less auth.log
```
 
Allows scrolling through large files interactively.
 
| Key       | Action           |
|-----------|------------------|
| Arrow keys| Scroll up/down   |
| /Failed   | Search for term  |
| q         | Quit             |
 
---
 
### head — View First Lines
 
```bash
head auth.log
head -n 20 auth.log
```
 
Shows the first 10 or 20 lines. Useful for checking the start of a log file.
 
---
 
### tail — View Last Lines
 
```bash
tail auth.log
```
 
Shows the last 10 lines.
 
Real-time monitoring:
 
```bash
tail -f auth.log
```
 
Continuously streams new log entries as they are written. Critical for detecting live attacks.
 
---
 
### Real SOC Scenario
 
Suspecting a brute force attack:
 
```bash
cd /var/log
tail -f auth.log
```
 
Output:
 
```
Failed password for admin from 192.168.1.10
Failed password for admin from 192.168.1.10
Failed password for admin from 192.168.1.10
```
 
---
