# ⚠️ Dovecot Empty Certificate with TLS SNI

Craft version (always up-to-date): https://www.craft.me/s/hQ33vvPcHsC4aA

README version (might be out of date):

If dovecot is throwing empty cert error when using TLS SNI

```bash
dovecot: imap-login: Error: Failed to initialize SSL server context: Can't load SSL certificate (ssl_cert setting): The certificate is empty
```

Make sure in your `/etc/dovecot/conf.d/10-ssl.conf` you have ssl_cert and ssl_key set **outside** the local block. This is for clients that do not support TLS SNI (Most should do except old ones)

Sources:

[Dovecot Documentation](https://doc.dovecot.org/configuration_manual/dovecot_ssl_configuration/#different-certificates-per-ip-and-protocol)

[Mail Archive](https://www.mail-archive.com/dovecot@dovecot.org/msg84353.html)
