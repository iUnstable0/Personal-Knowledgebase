# ⬇️ Installation

Craft version: https://www.craft.me/s/8ptIvnpSRFLgw8

Make sure there are no other certbot package installed

```bash
sudo apt purge *certbot*
```

**Make sure to not delete the directory `/etc/letsencrypt/live`**

Install `certbot`

```bash
snap refresh core
snap install certbot --classic
```
