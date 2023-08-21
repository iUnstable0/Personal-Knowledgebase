# ❌ Exit code 14 mongod.service

Craft version: https://www.craft.me/s/yGunTs6eY38MXT

To resolve mongod.service exit code 14, run this command:

```bash
sudo chown -R mongodb:mongodb /var/lib/mongodb
# Replace PORT_HERE with your mongoDB port
sudo chown mongodb:mongodb /tmp/mongodb-PORT_HERE.sock
```

This issue happens if you have previously ran mongod as root or another user.
