## Logrotate Configuration

To manage log rotation in a production‑like environment, a custom rule was created inside `/etc/logrotate.d/`.

### Objective
- Rotate application logs automatically  
- Compress old logs  
- Keep a defined number of log archives  
- Ensure logs are recreated with correct permissions  

---

## Logrotate Rule for `mi_servicio.log`

**File:** `/etc/logrotate.d/mi_servicio`

```txt
/home/dayarojas/mi_servicio.log {
    daily
    rotate 7
    compress
    missingok
    notifempty
    create 644 dayarojas dayarojas
}
```
Testing the Configuration
Simulate rotation (debug mode, no changes applied):
```
sudo logrotate -d /etc/logrotate.conf
```
Force rotation immediately:
```
sudo logrotate -f /etc/logrotate.conf
```

