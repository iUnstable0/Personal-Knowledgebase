# ❌ Cannot connect to storage server

Craft version: https://www.craft.me/s/HdnltOTGqRcm7p

This issue occurs when the Roundcube Plus Atlas client fails to connect to the SMTP/IMAP server.

Either check your configurations, try logging in from different mail client IP.

If both are fine then probably Fail2Ban blocking Roundcube Plus Atlas’s IP address for many failed login attempts from legitimate users.

This can also caused by invalid SSL certificate.
