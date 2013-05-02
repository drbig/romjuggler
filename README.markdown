# Rom Juggler

![Rom Juggler in action](https://raw.github.com/drbig/romjuggler/master/romjuggler.png)

A minimalist GUI front-end that is flexible and OS and emulator agnostic.

Features:

- Written in plain Java, tested under Linux (x64) and Windows 7 (i686)
- Data-driven UI (you define the platforms)
- Live filter by title and/or platforms
- Each platform can have different emulator command
- Human-friendly, well-commented config file

Bugs:

- Currently no support for emulator arguments
- Minimal-to-none error checking, expect NullPointerExceptions if you screw up the config file
- No caching, platform dirs scanned every time at startup (this may be a feature)

*If you like it - spread it!*

## Example config file

```
# This key is required. Only single words separated by single space,
# no trailing space. Case will be preserved across the GUI.
# The order in which you specify platforms will be the order in
# which games will be scanned and added to the table, as well as
# the order of platform checkboxes.
#
platforms=SNES NES N64 GB GBA SEGA MDRIVE PCE PSX ATARI C64

# For each platform you must specify the:
# -path, -exts and -cmd keys, starting with the name
# of the platform (which must be exactly as specified in
# the platforms key above).
#
# -path: path to the directory to scan for roms for the given
# platform, no trailing (back)slash
# -exts: string of file extensions to look for, without
# a dot, always lowercase and separated by a single space,
# no trailing space. Roms will be matched by their downcased 
# extension.
# -cmd: the absolute path to the command to be executed.
# The absolute path to the selected rom will be the only
# argument to the command.
# On Windows remember to escape the '\' character in paths
# by doubling it, e.g.:
# SNES-cmd=C:\\Program Files\\Mednafen\\mednafen.exe
#
SNES-path=/mnt/array/storage/games/snes
SNES-exts=zip smc
SNES-cmd=/usr/bin/mednafen

NES-path=/mnt/array/storage/games/nes
NES-exts=zip nes
NES-cmd=/usr/bin/mednafen

N64-path=/mnt/array/storage/games/n64
N64-exts=zip z64 v64 n64
N64-cmd=/usr/bin/mupen64plus

GB-path=/mnt/array/storage/games/gbc
GB-exts=zip gb
GB-cmd=/usr/bin/mednafen

GBA-path=/mnt/array/storage/games/gba
GBA-exts=zip gba
GBA-cmd=/usr/bin/mednafen

SEGA-path=/mnt/array/storage/games/sega
SEGA-exts=zip sms sg
SEGA-cmd=/usr/bin/mednafen

MDRIVE-path=/mnt/array/storage/games/megadrive
MDRIVE-exts=zip bin
MDRIVE-cmd=/usr/bin/mednafen

PCE-path=/mnt/array/storage/games/turbografx
PCE-exts=zip pce
PCE-cmd=/usr/bin/mednafen

PSX-path=/mnt/array/storage/games/psx
PSX-exts=cue
PSX-cmd=/usr/bin/mednafen

ATARI-path=/mnt/array/storage/games/atari
ATARI-exts=bin
ATARI-cmd=/usr/bin/hatari

C64-path=/mnt/array/storage/games/commodore
C64-exts=d64 t64 tap prg
C64-cmd=/usr/bin/x64
```

## Launching notes

On Windows you can double-click the .jar and it should work. On Linux, or form Window's command line, use: ```java -jar RomJuggler.jar```.
You can specify alternate config file as the first argument.
This requires Java SE 7, so if you get any Version exceptions at start you should update your JRE/JDK (you should anyway).

On Linux you'll probably want to have in your .bashrc:

```
export _JAVA_OPTIONS="-Dawt.useSystemAAFontSettings=on -Dswing.aatext=true"
```

This will enable font anti-aliasing in all Java apps (as long as they pick up the ENV you declared this variable in, of course). You're welcome.

On Windows you do need to escape the '\' character in paths (e.g. ```snes-cmd=C:\\Program Files\\Mednafen\\mednafen.exe```).

## Development notes

It works for me, if you want a feature/bug to be added either fork and code it yourself, or nag me via mail.
Any and all feedback will be appreciated!

## License

This work is licensed under a Creative Commons Attribution-NonCommercial 3.0 Unported License.
Lawyer-readable version [here](http://creativecommons.org/licenses/by-nc/3.0/legalcode).
