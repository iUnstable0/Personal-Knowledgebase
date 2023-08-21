# ☁️ Issue a certificate for domains under Cloudflare proxy

Craft version: https://www.craft.me/s/OVZP6RZ5rKJK0J

Refer to ⬇️ [Installation](craftdocs://open?blockId=E0C2F2F3-474E-4F6D-8BFD-A35F6127BE8F&spaceId=4805215e-be87-5f5f-cb68-33b0d48f82fe) for installing c`ertbot

Install `certbot-dns-cloudflare`

```bash
snap set certbot trust-plugin-with-root=ok
snap install certbot-dns-cloudflare
```

Edit the file `/root/.secrets/certbot/cloudflare.ini`

Fine-grained:

```other
# Cloudflare API token used by Certbot
dns_cloudflare_api_token = 0123456789abcdef0123456789abcdef01234567
```

Global:

```other
# Cloudflare API credentials used by Certbot
dns_cloudflare_email = cloudflare@example.com
dns_cloudflare_api_key = 0123456789abcdef0123456789abcdef01234
```

Secure the file by changing the permission

```bash
chmod -R 0700 /root/.secrets/
```

Now issue the cert

```bash
certbot certonly \
  --dns-cloudflare \
  --dns-cloudflare-credentials /root/.secrets/certbot/cloudflare.ini
```

If error, clear DNS cache (when certbots waiting for propagate)

```bash
systemctl restart bind9 # If you're using Bind9
systemctl restart systemd-resolved # Default resolver for most system
```

Tips: After you've updated the TXT record, make sure to clear your server's DNS cache before hitting enter and let certbot check the TXT record. Otherwise, certbot will fail to check the TXT record and you'll have to go through the whole process again.
