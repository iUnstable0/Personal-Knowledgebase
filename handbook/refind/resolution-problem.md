# 💻 Resolution problem

Craft version: https://www.craft.me/s/lroWSrKeyW2piA

If the graphics is stretched and zoomed in when booting with rEFInd, do this

Find section that starts with `# Launch specified OSes in graphics mode` in _`/boot/efi/EFI/refind/refind.conf`_ and uncomment the following line

```other
use_graphics_for osx,linux
```
