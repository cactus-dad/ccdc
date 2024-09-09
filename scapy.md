# scapy notes
## basic icmp packet dissection
```python
packetwin = IP(dst="<destination IP address>")/ICMP(type=8)
response = sr1(packetwin,timeout=2,verbose=True)
if response:
    if IP in response:
        ttl = response[IP].ttl
        # then we can create a list of windows and linux based on response size 64 for linux, 128 for windows
```