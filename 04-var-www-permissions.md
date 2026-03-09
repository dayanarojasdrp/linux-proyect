
# 04 — Correct Permissions for /var/www

##  Objective
Apply secure and professional permissions to a web project directory.

---

## 1. Create the project directory
```bash
sudo mkdir -p /var/www/myweb
```
## 2. Set ownership to the web server user
```bash
sudo chown -R www-data:www-data /var/www/myweb
```
## 3. Apply secure permissions
```bash
sudo chmod -R 755 /var/www/myweb
```
Verification
```bash
ls -ld /var/www/myweb
```
