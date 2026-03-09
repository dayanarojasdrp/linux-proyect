# Network Diagnostics (ARP, ICMP, Ports, Routes)

## ICMP Test (ping)
```bash
ping -c 3 8.8.8.8
```
## Routing Table
```bash
ip route
```
## ARP Table
```bash
ip neigh
```
## Port Scanning with netcat
```bash
nc -vz 192.168.64.2 22
nc -vz 192.168.64.2 80
```
