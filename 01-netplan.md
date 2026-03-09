# 01 — Static IP Configuration with Netplan

##  Objective
Configure a static IP address on Ubuntu Server using Netplan.

---

## 1. Locate your network interface
```bash
ip a
```
## 2.Edit the Netplan configuration
```bash
sudo nano /etc/netplan/01-netcfg.yaml
```
Example configuration:
```bash
network:
  version: 2
  renderer: networkd
  ethernets:
    ens18:
      dhcp4: no
      addresses:
        - *.*.*.*/*
      gateway4: *.*.*.*
      nameservers:
        addresses:
          - 8.8.8.8
          - 1.1.1.1

```
## 3. Apply the configuration
```bash
sudo netplan apply
```
Verification
```bash
ip a
ping -c 3 8.8.8.8

```
