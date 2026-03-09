
# 03 — Apache Web Server Setup

##  Objective
Deploy a basic website using Apache with a custom VirtualHost.

---

## 1. Install Apache
```bash
sudo apt update
sudo apt install apache2 -y
```
## 2. Create the project directory
```bash
sudo mkdir -p /var/www/myweb
echo "<h1>Hello from myweb</h1>" | sudo tee /var/www/myweb/index.html
```
## 3. Set correct permissions
```bash
sudo chown -R www-data:www-data /var/www/myweb
sudo chmod -R 755 /var/www/myweb
```
## 4. Create the VirtualHost
```bash
sudo nano /etc/apache2/sites-available/myweb.conf
```
Content:
```bash
<VirtualHost *:80>
    ServerName myweb.local
    DocumentRoot /var/www/myweb

    <Directory /var/www/myweb>
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/myweb_error.log
    CustomLog ${APACHE_LOG_DIR}/myweb_access.log combined
</VirtualHost>
```
## 5. Enable the site
```bash
sudo a2ensite myweb.conf
sudo a2dissite 000-default.conf
sudo systemctl reload apache2
```

