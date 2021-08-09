# copy-paste firefox broken on Ubuntu 21.04

Copy-paste doesn't work w/ Firefox and or Diodon etc.

Well Ubuntu 21.04 codename: hirsute (hippopotamous) doesn't use X11 as default for its user but [Wayland][1]
and [Firefox][2] has problems with it; [Zoom][3] has problems with it too !


[Wayland][5] vs. [X11/Xorg][6]  : what is the difference :a [read more...][7]
So until the fix their respective issues, you can change the default back to Xorg :

```sh
sudoedit /etc/gdm3/custom.conf
```

[1]: https://www.omgubuntu.co.uk/2021/01/ubuntu-21-04-will-use-wayland-by-default
[2]: https://duckduckgo.com/?q=problem+wayland+firefox
[3]: https://duckduckgo.com/?q=problem+zoom+on+wayland
[4]: about:about
[5]: https://wayland.freedesktop.org/
[6]: https://www.x.org/wiki/
[7]: https://linuxiac.com/xorg-x11-wayland-linux-display-servers-and-protocols-explained/
[8]: https://www.askvg.com/tip-list-of-all-hidden-secret-internal-pages-and-urls-in-chrome-firefox-and-microsoft-edge/
