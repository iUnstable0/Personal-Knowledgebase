# 🤖 Certificate auto-renewal with cronjob

Craft version: https://www.craft.me/s/VgstDKH490T0Ue

Enter the editor

```bash
crontab -e
```

Twice a day at 3:30 AM and 3:30 PM:

```other
30 3,15 * * * /snap/bin/certbot renew --quiet
```

Daily:

```other
@daily /snap/bin/certbot renew --quiet
```

What I currently use (With email server setup & mongoDB server)

```bash
@daily /snap/bin/certbot renew --quiet && /bin/bash /root/certbot-renew.sh > /de
v/null 2>&1
```

`certbot-renew.sh`

This script merges the certbot certificate fullchain and privkey to use with MongoDB server as it doesnt support seperate fullchain and privkey

It also updates the sni_maps and reload postfix and dovecot after certficiate renewal and sends an email notification.

Edit this to your likings

```bash
#!/bin/bash

CERT_DIR="/etc/letsencrypt/live/domain.tld"  # Update with your actual certificate directory
CERT_FILE="/etc/ssl/mongodb.pem"  # Update with the path to your MongoDB certificate file

# Combine the certificate files
NEW_CERT_CONTENT=$(cat "$CERT_DIR/privkey.pem" "$CERT_DIR/fullchain.pem")

# Check if the certificate file exists or is different
if [[ ! -f "$CERT_FILE" || "$NEW_CERT_CONTENT" != "$(cat "$CERT_FILE")" ]]; then
    MESSAGE="Certificate has been updated. Updating $CERT_FILE and restarting mongod..."
    echo "$NEW_CERT_CONTENT" > "$CERT_FILE"
    systemctl restart mongod
else
    MESSAGE="Certificate is unchanged. No restart necessary."
fi

# Assuming that you setup TLS SNI, if not then comment this out
/usr/sbin/postmap -F /etc/postfix/sni_maps

# Reload Postfix and Dovecot
systemctl reload postfix dovecot

# Email subject (replace de-01 with your system name or jus remove it)
# i used de-01 cuz the VPS is in Germany and I got multiple in different regions
# so its easy for me to tell which email is from which region)
SUBJECT="de-01: Certificate merger status"

# From header
FROM="System <no-reply@domain.tld>"

# Send the email (Make sure sendmail is installed)
/usr/sbin/sendmail -oi -t <<EOF
From: $FROM
To: your_email@domain.tld
Subject: $SUBJECT

$MESSAGE
EOF
```
