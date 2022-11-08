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
- Verify Certificate validity. Run as none `root` user
```
certbot certificates
```

If you receive `[Errno 13] Permission denied: '/var/lib/letsencrypt/.certbot.lock'` error message, run
```
sudo chown fred:fred /var/lib/letsencrypt/ -R

```
Rerun ` cerbot` or `certbot certificates` again. You shoud see something like this:

```bash
Saving debug log to /var/log/letsencrypt/letsencrypt.log

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Found the following certs:
  Certificate Name: example.net
    Serial Number: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
    Key Type: RSA
    Domains: example.net
    Expiry Date: 2023-01-16 20:24:54+00:00 (VALID: 68 days)
    Certificate Path: /etc/letsencrypt/live/example.net/fullchain.pem
    Private Key Path: /etc/letsencrypt/live/example.net/privkey.pem
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
```
- Set `certbot` to automatically update certificates. To do so, run,
```
crontab -e
```
and set `0 12 * * * /usr/bin/certbot renew --quiet`. This will check certificates lifecycle and update it when they are due.