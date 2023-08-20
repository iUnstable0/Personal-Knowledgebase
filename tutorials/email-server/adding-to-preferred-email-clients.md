# 📬 Adding to preferred email clients

NOTES: this is documentation for my self-hosted email server (i followed linuxbabe tutorial)

View the Craft version [here](https://www.craft.me/s/E51vyDkFldnu5D) (latest)

ReadME version might be outdated:

**IMAP Settings:**

- Host: `mail.domain.tld`
- Port: `143` (non-secure connection) or `993` (secure connection)

**SMTP Settings:**

- Host: `mail.domain.tld`
- Port: `465` (Implicit SSL/TLS) or `587` (Explicit SSL/TLS)

**For a secure and reliable connection, we suggest using the second port option (`993` for IMAP and `587` for SMTP).**

**Username Format:**

- Include `@domain.tld` in your username. For instance, `johndoe` should be `johndoe@domain.tld`.
