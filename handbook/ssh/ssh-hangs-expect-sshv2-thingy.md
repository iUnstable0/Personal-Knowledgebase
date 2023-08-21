# ⌛ SSH Hangs Expect SSHV2 Thingy

Craft version: https://www.craft.me/s/1sCcONqM7L0Bzt

Change the network interface MTU to solve it.

Run either command:

```bash
sudo ip li set mtu 1400 dev eno2
```

```bash
sudo ifconfig eno2 mtu 1400
```

Remember to replace `eno2` with your network interface name.
You can list it with `ip link`

If that doesn't work, try `1200` instead.
