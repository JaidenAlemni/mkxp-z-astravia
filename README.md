# mkxp-z - Legends of Astravia Fork

This is a fork of **[mkxp-z](https://github.com/mkxp-z/mkxp-z)** created for use in [Legends of Astravia](https://www.astraviagame.com/). *Most* dependencies have also been copied over to my personal account.

**It is highly advised you don't fork from this repo as changes are done exclusively to support my game and its development.** Of course, you are welcome to reference, cherry-pick, etc. at your leisure. I also am not your dad and can't tell you what to do, just know I won't do anything about it if it doesn't work / break / etc. in anything outside of LoA.

Please refer to the original mkxp-z repo for additional info, forking yourself, etc.

---

<p align="center"><b>
  <a href="https://github.com/JaidenAlemni/mkxp-z-astravia/releases">Releases</a>
  ・
  <a href="https://github.com/JaidenAlemni/mkxp-z-astravia/actions/workflows/autobuild.yml">Automatic Builds</a>
  ・
  <a href="https://github.com/JaidenAlemni/mkxp-z-astravia/wiki">Docs</a>
</b></p>

---

## Dependency Info

| Local | Name | Location | Version | Purpose |
| --- | --- | --- | --- | --- |
| ✅ | ruby | JaidenAlemni/ruby | 3.1.6 | Game scripts ❤ |
| ✅ | SDL2 | JaidenAlemni/SDL | 2.30.1 | mkxp's blood and guts |
| ✅ | SDL_image | JaidenAlemni/SDL_image | 2.6.3 | Image library for SDL |
| ❌ | libpng | pnggroup/libpng | 1.6.50 | SDL_Image dependency |
| ❌ | libjpeg | mkxp-z/libjpeg-turbo | ? | SDL_Image dependency |
| ✅ | SDL_Sound | JaidenAlemni/SDL_sound | 2.0.1 | Soundfile decoding library |
| ❌ | Theora | xiph/theora | 1.2.0alpha1 | Video playback |
| ✅ | Vorbis | JaidenAlemni/vorbis | 1.3.7 | Theora+SDL_sound dependency |
| ✅ | libogg | JaidenAlemni/ogg | 1.3.5 | Theora+SDL_sound dependency |
| ✅  | OpenAL | JaidenAlemni/openal-soft | 1.22.2 | 3D Audio API |
| ✅ | SDL_ttf | JaidenAlemni/SDL_ttf | 2.0.15(?) | TTF Font library for SDL |
| ✅ | Freetype | JaidenAlemni/freetype2 | 2.13.0 | SDL_ttf dependency |
| ❌ | fluidsynth | mkxp-z/fluidsynth-sans-glib | 2.0.3 | MIDI synthesizer |
| ✅ | PhysFS | JaidenAlemni/physfs | 3.2.0 | Archive I/O |
| ❌ | uchardet | mkxp-z/uchardet | 0.0.6 | Text encoding |
| ❌ | pixman | mkxp-z/pixman | 0.38.0 | Image compositing API |
| ❌ | OpenSSL | openssl/openssl | 1.1.1 | HTTPS n' stuff |



## Credit and Thanks

+ Ancurio, for mkxp
+ zorua / Struma, for mkxp-z
+ Eblo & KK20, for extra help and fixes
+ Other contributors:
+ Savordez, Aeodyn, Splendide Imaginarius, WaywardHeart, hatkid, PieGod
+ and anyone else who has made contributions / fixes that I've poached from to make things work

## Other Notes

### Debugging with vscode in Windows

1. After installing msys2, install some more stuff:
```bash
pacman -S --needed base-devel mingw-w64-ucrt-x86_64-toolchain
```
2. Build like normal, except set `-Ddebug=true` with meson
3. Create a launch.json in .vscode with the following stuff
```json
"version": "0.2.0",
"configurations": [
    {
        "name": "(gdb) Launch",
        "type": "cppdbg",
        "request": "launch",
        "program": "C:\\directory\\with\\your\\game.exe",
        "args": ["debug"],
        "stopAtEntry": false,
        "cwd": "${fileDirname}",
        "environment": [],
        "externalConsole": false,
        "MIMode": "gdb",
        "setupCommands": [
            {
                "description": "Enable pretty-printing for gdb",
                "text": "-enable-pretty-printing",
                "ignoreFailures": true
            },
            {
                "description": "Set Disassembly Flavor to Intel",
                "text": "-gdb-set disassembly-flavor intel",
                "ignoreFailures": true
            }
        ]
    }
]
```
Most of these are default, the big one is `"cwd": "${fileDirname}"`, which is a little misleading--even if your .exe is in your game folder somewhere else, this needs to be set to this value.