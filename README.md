acme-tiny-run
------

A script to automate and run the acme-tiny script

## Usage

acme-tiny-run /path/to/acme-tiny-dir /path/to/key-and-cert-store uri-to-register /path/to/uri/challenge-dir

## How to set up

```bash
cd /opt
git clone https://github.com/diafygi/acme-tiny.git
git clone https://github.com/JamesBarwell/acme-tiny-run.git
```

```bash
# vim /opt/update-certificates

# Duplicate this line per domain/subdomain
/opt/acme-tiny-run/acme-tiny-run /opt/acme-tiny /etc/ssl/letsencrypt example.com /var/www/example.com/public/.well-known/acme-challenge

# Reload web server
/etc/init.d/nginx reload
```

```bash
chmod u+x /opt/update-certificates
echo "0 0 1 * * /opt/update-certificates >> /var/log/acme_tiny.log" >> /etc/crontab
```
