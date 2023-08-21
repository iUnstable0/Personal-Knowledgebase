# 🔁 Fix redirect behind reverse proxy

Craft version: https://www.craft.me/s/9RWuS1mRdIEI01

README version (might be out of date):

Edit `/etc/webmin/config`

```conf
webprefixnoredir=1
relative_redir=0
referers=subdomain.domain.com
```

Edit `/etc/webmin/miniserv.conf`

```conf
ssl=1
redirect_port=443
```
