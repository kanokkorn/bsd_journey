Desktop Environment
===

This section will cover how to get a desktop environment up and running on FreeBSD 13.1

Prerequisite
---

- `xorg` for graphical server
- `ly` for login screen
- `bspwm` for tilting window manager
- `sxhkd` for keyboard event hanlder
- `rxvt-unicode` for terminal
- `sndio` for sound server

X server
---

once `xorg` already installed, try `startx` to check if xserver is working properly. After that we can start config xserver.

first create new file callled `.xinitrc` in home directory and set permission using `chmod` with `775` for root and local user to be read, write and excute file but group can be ignore.

```sh
#!/bin/sh

# this file will run when pass a login screen

```

Font
---

Default font come will Xserver is monospace font and may not support UTF-8, to check all avaliable font use `fc-list` and all installed font will be output to console.

Font name can be find using `grep` and pipe with `fc-list`, for example

```sh
# find Monospace font
fc-list | grep Mono
```

Rxvt-unicode
---

`Rxvt-unicode` or `urxvt`is fast, robust and lightweight among sea of terminal emulator

Terminal can be customize with file called `.Xsession` that can be create and place in home directory

Ly
---

A better login screen compare to default one. It provide options to switch between desktop environment if installed more than one on system.

For config ly to running at startup, first add these following line to `/etc/gettytab`

```sh
Ly:\
  :lo=/usr/local/bin/ly:\
    :al=root:
```

also, modify `ttyv1` to example below for terminal entry in `/etc/ttys`

```sh
ttyv1   "/usr/libexec/getty Ly"         xterm   on secure
```

sndio
---

Sound server written for OpenBSD but has been port to variety of BSD, it's lightweight and provide per-application volume control.

Usually come bundle with Chromium or Firefox

