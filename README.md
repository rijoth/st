# Rijo's build of st - the suckless terminal

st is a simple terminal emulator for X which sucks less.

# About this fork
This is a fork of st, the original repo can be found here: [https://git.suckless.org/st/](https://git.suckless.org/st/)
The original st webpage is here: [https://st.suckless.org/](https://st.suckless.org/)

### Patches applied
* (st-gruvbox)[https://st.suckless.org/patches/gruvbox/]
* (scrollback)[https://st.suckless.org/patches/scrollback/]

### Extra features of this fork.
+ **scrollback** support with `alt-↑/↓` or `alt-pageup/down` or `shift` while scrolling the
  mouse.
+ OR **vim-bindings**: scroll up/down in history with `alt-k` and `alt-j`
+ *zoom/change font size**: same bindings as above, but holding down shift as
  well. `alt-home` returns to default

## Requirements
In order to build st you need the Xlib header files.

## Installation
Edit config.mk to match your local setup (st is installed into the /usr/local namespace by default).
Afterwards enter the following command to build and install st (if necessary as root):
```bash
make clean install
```

## Running st

If you did not install st with make clean install, you must compile
the st terminfo entry with the following command:

```bash
tic -sx st.info
```

## Credits
* Forked from [https://st.suckless.org/](https://st.suckless.org/)
* Based on Aurélien APTEL aurelien.aptel@gmail.com bt source code.
