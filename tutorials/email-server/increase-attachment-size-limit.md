# 📁 Increase attachment size limit

Craft version https://www.craft.me/s/J21kvXViGeJbZ2

## Postfix

Check the limit

```bash
postconf | grep message_size_limit
```

Change the limit

```bash
# 104857600 Bytes = 100MB
postconf -e message_size_limit=104857600
```

Restart Postfix

```bash
systemctl restart postfix
```

## NGINX

Inside the server config block, set this:

```bash
client_max_body_size 100M;
```

Restart `nginx`

```bash
nginx -t
systemctl restart nginx
```

## PHP

`cd` into `/etc/php/x/fpm` (Replace `x` with the version, ex: `8.2`)

```bash
cd /etc/php/x/fpm
```

Edit the file `php.ini`

```bash
nvim php.ini
```

Locate these configs and change it to your preferred size

```bash
upload_max_filesize = 100M
post_max_size = 100M
```

**Don't forget to change on the atlas customers control panel if you're using Roundcube Plus Atlas!**
