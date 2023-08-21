# 👂🏻 Allow Caddy to listen to privileged ports

Craft version: https://www.craft.me/s/xoCMRhUvb9iEfJ

To allow Caddy to listen to privileged ports, run this:

```bash
setcap 'cap_net_bind_service=+ep' /usr/bin/caddy
```
