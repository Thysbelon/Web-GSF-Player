# Web-GSF-Player
Work in progress. Will play GSF files in the browser.

The `docs` folder contains compiled gsf2wav js and wasm binaries, as well as a [demo page](https://thysbelon.github.io/Web-GSF-Player).

@jprjr created lazygsf and gsf2wav.

The mgba CMakeLists.txt threads modification was copied from [@jprjr's fork](https://github.com/mgba-emu/mgba/pull/2065),    
and the Emscripten modifications were copied from [mgba's feature/wasm branch](https://github.com/endrift/mgba/blob/feature/wasm/CMakeLists.txt).   
The modifications to mgba's CMakeLists.txt allow libmgba.a to be compiled with Emscripten, threads disabled and MINIMAL_CORE set to 2.

The lazygsf CMakeLists.txt modifications call mgba's CMakeLists.txt instead of manually including sources; the goal of this modification was to make it easier to update mgba to the latest version.

Right now, the mgba 0.10.2 release build is being used.

## How to Build
1. Use Linux
2. Download [gsf2wav](https://github.com/jprjr/gsf2wav)
3. go to the gsf2wav folder
4. make sure [lazygsf](https://github.com/jprjr/lazygsf/) is in the lazygsf folder
5. go to the mgba folder in the lazygsf folder.
6. replace the contents of the mgba folder with the source code of the [mgba 0.10.2 release](https://github.com/mgba-emu/mgba/tree/0.10.2).
7. download the source code of this repository
8. place the contents of this repository (except the `docs` folder and the `README.md` file) in gsf2wav; this will replace the CMakeLists.txt files of gsf2wav, lazygsf and mgba with my modified copies.
9. build with Emscripten's `emcmake`
