### Install and Troubleshoot Certbot# 

- Grant `nodeuser ` access to `certbot` file.
```
sudo chown fred:fred /usr/bin/certbot -R
```

- Grant `nodeuser` access to certificate directories and files
```
cd /etc/letsencrypt/live/fredgentech.net/ 

sudo chown fred:fred /usr/bin/certbot -R
sudo chown fred:fred /var/log/letsencrypt/ -R
sudo chown fred:fred  /etc/letsencrypt/live/fredgentech.net/ -R
sudo chmod +x /etc/letsencrypt/fredgentech.net/
sudo chmod +x /etc/letsencrypt/archive
sudo chown fred:fred  /etc/letsencrypt/live -R
sudo chown fred:fred ../../archive/fredgentech.net/privkey1.pem* -R
```

