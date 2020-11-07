sway-xkb-switcher
===============

## Description

sway-xkb-switcher records keyboard layout for a sway windows when you leave them.
And when you come back it is restore keyboard layout.

This project is forked from https://github.com/inn0kenty/i3-xkb-switcher
and adapted to work with sway window manager.

There is also helper switcher for emacs.

On layout switch event emacs-sway-xkb tool checks
if focused window is emacs window.
In case of emacs window it switches emacs input method.

In case of non-emacs window,
emacs-sway-xkb switches wayland keyboard layout.

NOTE: emacs-sway-xkb is able to only detect emacs native window.
If you open emacs frame in terminal,
it will not detect it.

## Install

```bash
$ pip install sway-xkb-switcher
```

Also you can download compiled binary from [release page](https://github.com/nmukhachev/sway-xkb-switcher/releases).

## Usage

### sway-xkb-switcher

```bash
$ sway-xkb-switcher --input-identifier <identifier>
```

You can view a list of actual identifiers by looking at

```bash
$ swaymsg -t get_inputs | grep identifier
```
The identifier corresponds to that from the input section of your sway config.

To enable debug mode run with `--debug` key.

By default it writes logs to stdout. You can specify path by `--log-path` option.

### emacs-sway-xkb

If you are using emacs you can
keep emacs with its own state of input method.

Bind some key to switch keyboard layout and
completely disable xkb native switching option
in your sway config file.

```
input "1:1:AT_Translated_Set_2_keyboard" {
  xkb_layout us,ru
#  xkb_options grp:alts_toggle,shift:both_capslock
}

bindsym --to-code $mod+n exec emacs-sway-xkb
```
