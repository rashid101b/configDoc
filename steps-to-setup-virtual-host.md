### 1) Create a User
```
sudo adduser --home <path> --gid 100 <User-name>
e.g.
sudo adduser --home /var/www/trmt.ebslab.com --gid 100 trmt
Enter password : kowtavdu
```
### 2) Create a subdomain to godaddy

trmt.ebslab.com

### 3) Configure Virtual Host

```
cd /etc/apache2/sites-available/
cp 000-default.conf subdomain.website.conf
e.g.
sudo cp transroman.ebslab.com.conf trmt.ebslab.com.conf

sudo apache2ctl configtest
a2ensite trmt.ebslab.com.conf

reload/restart the apache2 server 
sudo systemctl reload apache2
sudo service apache2 restart
sudo systemctl restart apache2
```
Note: a2dissite disables a site by removing those symlinks

check in browser
### 4) Setup index page
```
sudo su --login <user-name>
e.g.
sudo su --login trmt
```
xx) How to add letus encrypt
```
sudo certbot --apache -d transzaar.ebslab.com
```
ERROR
if subdomain is not working check your firewall.
The default firewall configuration tool for Ubuntu is ufw


see below URL
https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-20-04
