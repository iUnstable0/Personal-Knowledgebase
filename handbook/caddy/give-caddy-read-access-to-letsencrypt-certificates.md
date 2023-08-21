# 🪪 Give Caddy read access to LetsEncrypt certificates

Craft version: https://www.craft.me/s/kAI0ZywWW741oT

Make sure the package `acl` is installed

```bash
sudo apt update
sudo apt install acl
```

To give Caddy read access, run this:

```bash
sudo setfacl -R -m u:caddy:rx /etc/letsencrypt/live/ /etc/letsencrypt/archive/
```
