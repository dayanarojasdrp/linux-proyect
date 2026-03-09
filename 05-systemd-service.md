
# 05 — Creating a Custom systemd Service

##  Objective
Create a real systemd service that runs a script automatically.

---

## 1. Create the script
```bash
sudo mkdir -p /opt/scripts
sudo chown user:user /opt/scripts
nano /opt/scripts/script.sh
```
Content:
``` bash
#!/bin/bash
echo "$(date) - Service executed" >> /home/user/service.log
```
Make executable:
```bash
sudo chmod +x /opt/scripts/script.sh
```
## 2. Create the systemd service
``` bash
sudo nano /etc/systemd/system/myservice.service
```
Content:
```
[Unit]
Description=Custom systemd service example
After=network.target

[Service]
Type=simple
ExecStart=/opt/scripts/script.sh
User=user
Group=group
Restart=on-failure

[Install]
WantedBy=multi-user.target
```
## 3. Enable and start the service
```bash
sudo systemctl daemon-reload
sudo systemctl enable myservice.service
sudo systemctl start myservice.service
```
Verification
``` bash
systemctl status myservice.service
sudo journalctl -u myservice.service -f
```
