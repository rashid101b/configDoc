# configDoc
### Step 1: Install the CGI Module
sudo apt-get install libapache2-mod-cgi

### Step 2: Enable the CGI Module
sudo a2enmod cgi

### Step 3: Configure Apache to Execute CGI Scripts

Do the change for CGI enabled in /ete/apache2/site-availables/<sub-domain.conf>

```
ScriptAlias /cgi-bin/ /var/www/transacct.ebslab.in/public_html/cgi-bin/
<Directory /var/www/transacct.ebslab.in/public_html/cgi-bin/>
	#AllowOverride None
    	Allow from all
    	Require all granted
    	Options ExecCGI 
	AddHandler cgi-script .cgi .pl .py
	</Directory>

RewriteEngine on
RewriteCond %{SERVER_NAME} =transacct.ebslab.in
RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]
```
remove ssl file <subdomain-domain>-le-ssl.conf if already exist and create a new one
sudo certbot --apache -d <subdomain-domain>.in/.com
Note: if you do any change in <subdomain-domain>.conf file them delete "<subdomain-domain>-le-ssl.conf" and generate newone.

###  Step 4: Restart Apache
sudo systemctl restart apache2 

###  Step 5 : create any python/perl/cgi program to execute in browser.
5.1 ) Create python file (test.py) and paste the below program into it and save it in path </var/www/<subdomain.domain>/cgi-bin>
```
#!/usr/bin/python3
print ("Content-type: text/html")
print ("")
print ("")
print ("<html><head>")
print ("")
print ("</head><body>")
print ("Hurrah! CGI is working using python")
print ("</body></html>")
```
5.2 ) Create python file (test.pl) and paste the below program into it and save it in path </var/www/<subdomain.domain>/cgi-bin>
```
#!/usr/bin/perl
print "Content-type: text/html\n\n";
print "Hurrah! CGI program is running using perl.";

```

###  Step 6 : open browser and type the below command to see the output
https://<subdomain-domain>/cgi-bin/<test>.py/.pl/.cgi
e.g.
https://transacct.ebslab.in/cgi-bin/test.py


* line1
* line2

---
Create by Rashid Ahmad
