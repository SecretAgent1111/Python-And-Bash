# What is Threat Intelligence?
 
Threat intelligence means checking whether an indicator — an IP, domain, or file hash — is known to be malicious. In SOC, this is done automatically by querying services like VirusTotal, AbuseIPDB, and AlienVault OTX.
 
---
 
### Install the requests Library
 
```
pip install requests
```
 
---
 
### Real Threat Intel Query (AbuseIPDB)
 
```python
import requests
 
ip      = "8.8.8.8"
api_key = "YOUR_API_KEY"
 
url = "https://api.abuseipdb.com/api/v2/check"
 
headers = {
    "Key": api_key,
    "Accept": "application/json"
}
 
params = {
    "ipAddress": ip,
    "maxAgeInDays": 90
}
 
response = requests.get(url, headers=headers, params=params)
 
data = response.json()
 
print(data)
```
 
---
 
### Mock SOC Logic Example (for Learning)
 
```python
def check_ip(ip):
    print(f"Checking {ip}...")
 
    if ip == "8.8.8.8":
        return "Clean"
    else:
        return "Suspicious"
 
ips = ["8.8.8.8", "192.168.1.5"]
 
for ip in ips:
    result = check_ip(ip)
    print(ip, "->", result)
```
 
Output:
 
```
Checking 8.8.8.8...
8.8.8.8 -> Clean
Checking 192.168.1.5...
192.168.1.5 -> Suspicious
```
 
---
