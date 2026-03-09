# 02 — Secure SSH Configuration

##  Objective
Harden SSH access by:
- Creating a non-root user
- Changing the SSH port
- Enabling key-based authentication
- Disabling password login

---

## 1. Create a new user
```bash
sudo adduser user
sudo usermod -aG sudo user
```
## 2. Edit SSH configuration
```bash
sudo nano /etc/ssh/sshd_config
```
Modify:
```bash
Port **
PermitRootLogin no
PasswordAuthentication no
```
## 3.Copy SSH keys 
```bash
ssh-copy-id -p ** user@*.*.*.*
```
## 4. Restart SSH
```bash
sudo systemctl restart ssh
```
Verification
```bash
ssh -p ** user@*.*.*.*
```
