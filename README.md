# libde265.js

Pure JavaScript HEVC/H.265 video decoding library using libde265.

Compiled from libde265 v1.0.2 using Emscripten. Should run in all
current browsers like Google Chrome 33+, Firefox 28+, IE 11+, Opera
20+ and Safari 7+ on OSX Mavericks. Older versions might work, but
this is mostly untested.

NOTE: This is a very early preview which needs more testing and lots
of optimizations!

## Changes

Added `RawPlayer.set_framerate(fps)` to allow setting of desired
playback framerate, e.g. 30, so that frames are not always decoded
and displayed at full speed.

## Building

(currently only tested on Linux and Mac)

- Install [Emscripten][1] and put into your `PATH`
- Execute the `build.sh`, this will download and compile libde265 using
  Emscripten and will generate the `libde265.js` file.
- If the version of your default LLVM is below 3.2, you might need to
  install the package `llvm-3.2` (or newer) and set the environment
  variable `LLVM_ADD_VERSION` to `3.2` (or whatever you installed).

(built on Mac using Emscripten 1.36.5):

```
emcc (Emscripten gcc/clang-like replacement + linker emulating GNU ld) 1.36.5
clang version 3.9.0  (emscripten 1.36.5 : 1.36.5)
Target: x86_64-apple-darwin15.6.0
Thread model: posix
InstalledDir: /usr/local/opt/emscripten/libexec/llvm/bin
```

## Examples

A small example can be found in the `demo` folder and on
https://strukturag.github.io/libde265.js/.

## Known issues

- **Minified version has broken using latest Emscripten**
- More code from libde265 should be made asm.js aware
- Decoding should be made asynchronous through WebWorkers where available

[1]: http://emscripten.org

Copyright (c) 2014 struktur AG
