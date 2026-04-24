# Rijo's build of st - the simple (suckless) terminal

The [suckless terminal (st)](https://st.suckless.org/) with some additional
features that make it literally the best terminal emulator ever:

## Unique features (using external scripts)

+ **follow urls** by pressing `alt-l` (opens URL in browser via st-urlhandler)
+ **copy urls** in the same way with `alt-y`
+ **copy visible terminal output** with `alt-o`

## Keybindings

### Scrollback
+ `alt-↑/↓` or `alt-pageup/pagedown` - scroll by page
+ `alt-k/j` - scroll up/down by one line (vim-style)
+ `alt-u/d` - scroll up/down by half page (vim-style)
+ Mouse wheel scrolling works with shift held

### Zoom / Font Size
+ `shift-alt-↑/↓` or `shift-alt-k/j` - increase/decrease font size
+ `shift-alt-u/d` - increase/decrease font size faster
+ `shift-alt-home` - reset to default font size

### Copy & Paste
+ `alt-c` or `ctrl-alt-c` - copy selection to clipboard
+ `alt-v` or `ctrl-alt-v` - paste from clipboard
+ `shift-insert` - paste from primary selection
+ Mouse selection automatically copies to clipboard

### Transparency
+ `alt-s` - decrease transparency (more opaque)
+ `alt-a` - increase transparency (more transparent)

### Other
+ `ctrl-print` - print screen
+ `shift-print` - print selected text

## Pretty stuff

+ Compatibility with `Xresources` and `pywal` for dynamic colors.
+ Default [gruvbox](https://github.com/morhetz/gruvbox) colors.
+ Transparency/alpha (default 80% opaque), adjustable via Xresources or keybindings.
+ Default font: **JetBrains Mono** at 18pt with **NotoColorEmoji** as fallback for emojis.
+ Border width: 2px

## Implemented st patches

+ **boxdraw** - Render box drawing characters (U2500-U259F) without font
+ **ligatures** - Harfbuzz-based ligature support (fi, fl, etc.)
+ **font2** - Alternative font for emojis/symbols
+ **alpha** - Background opacity/transparency control
+ **urlhandler** - Clickable URLs with external handler script
+ **copyoutput** - Copy visible terminal content to clipboard
+ **scrollback** - Extended scrollback buffer (10,000 lines)
+ **auto-clipboard** - Automatic copy to CLIPBOARD on mouse selection

## Installation

You need the following dependencies:
- `libX11`
- `libXft`
- `libXrender`
- `fontconfig`
- `freetype`
- `harfbuzz`

```bash
git clone https://github.com/rijosm/st
cd st
make
sudo make install
```

On OpenBSD, be sure to edit `config.mk` first and remove `-lrt` from the
`$LIBS` before compiling.

Be sure to have a composite manager (`xcompmgr`, `picom`, etc.) running if you
want transparency.

## How to configure dynamically with Xresources

For many key variables, this build of `st` will look for X settings set in
either `~/.Xdefaults` or `~/.Xresources`. You must run `xrdb` on one of these
files to load the settings.

For example, you can define your desired fonts, transparency or colors:

```
*.font:        JetBrains Mono:pixelsize=14:antialias=true:autohint=true;
*.fontalt0:    NotoColorEmoji:pixelsize=12:antialias=true:autohint=true;
*.alpha:       0.9
*.color0:      #282828
*.color1:      #cc241d
...
```

The `alpha` value (for transparency) goes from `0` (transparent) to `1`
(opaque).

### Colors

To be clear about the color settings:

- This build will use gruvbox colors by default and as a fallback.
- If there are Xresources colors defined, those will take priority.
- But if `wal` has run in your session, its colors will take priority.

Note that when you run `wal`, it will negate the transparency of existing windows, but new windows will continue with the previously defined transparency.

## Default Configuration

| Setting | Value |
|---------|-------|
| Font | JetBrains Mono 18pt |
| Fallback Font | NotoColorEmoji 14pt |
| Border | 2px |
| Background Alpha | 0.8 (80% opaque) |
| Scrollback | 10,000 lines |
| Cursor | Block |
| Bell Volume | 0 (off) |

## Contact

- Rijo Smamantha <rijo@rijo.in>
- [https://rijo.in](https://rijo.in)