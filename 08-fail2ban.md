## Fail2ban Configuration

Fail2ban was installed and configured to protect the server from SSH brute‑force attacks.

### Jail configuration (`/etc/fail2ban/jail.local`)

```ini
[sshd]
enabled = true
port = 2222
filter = sshd
logpath = /var/log/auth.log
maxretry = 5
bantime = 10m
```
Service status
```
sudo systemctl status fail2ban
```
