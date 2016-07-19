acme-tiny-run
------

A script to automate and run the acme-tiny script

## Usage

```
acme-tiny-run /path/to/acme-tiny-dir /path/to/key-and-cert-store uri-to-register /path/to/uri/challenge-dir
```

* acme-tiny-dir is where the acme-tiny git repo has been checked out
* key-and-cert-store is where you will store your account keys, domain keys and certificates
* uri-to-register is your website's URI
* challenge-dir is a directory inside your website's public root, which your webserver must serve at the path "/.well-known/acme-challenge"

## How to set up

```bash
cd /opt
git clone https://github.com/diafygi/acme-tiny.git
git clone https://github.com/JamesBarwell/acme-tiny-run.git
```

```bash
# create file /opt/update-certificates with the following content:

# Duplicate this line per domain/subdomain
/opt/acme-tiny-run/acme-tiny-run /opt/acme-tiny /etc/ssl/letsencrypt example.com /var/www/example.com/public/.well-known/acme-challenge

# Reload web server
/etc/init.d/nginx reload
```

```bash
chmod u+x /opt/update-certificates
echo "0 0 1 * * /opt/update-certificates 2>> /var/log/acme_tiny.log" >> /etc/crontab
```
