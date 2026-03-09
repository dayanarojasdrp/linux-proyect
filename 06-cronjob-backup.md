
# 06 — Automated Backup with Cron

##  Objective
Create a daily backup of `/var/www/myweb` using a cronjob.

---

## 1. Create the backup script
```bash
nano /opt/scripts/backup-myweb.sh
```
Content:
```
#!/bin/bash
FECHA=$(date +%F)
ORIGIN="/var/www/myweb"
DESTINATION="/var/backups/myweb-$FECHA"

mkdir -p $DESTINATION
cp -r $ORIGIN/* $DESTINATION/

echo "$(date) - Backup created at $DESTINATION" >> /var/log/backup-myweb.log
```
Make executable:
```bash
sudo chmod +x /opt/scripts/backup-myweb.sh
```
## 2. Create the cronjob
```bash
crontab -e
```
Add:
```bash
0 2 * * * /opt/scripts/backup-myweb.sh
```
