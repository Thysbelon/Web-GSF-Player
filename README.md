# Web-GSF-Player
Work in progress. Will play GSF files in the browser.

@jprjr created lazygsf and gsf2wav.

The mgba CMakeLists.txt threads modification was copied from [@jprjr's fork](https://github.com/mgba-emu/mgba/pull/2065).
The modifications to mgba's CMakeLists.txt allow libmgba.a to be compiled with threads disabled and MINIMAL_CORE set to 2.

The lazygsf CMakeLists.txt modifications call mgba's CMakeLists.txt instead of manually including sources; the goal of this modification was to make it easier to update mgba to the latest version.

Right now, the mgba 0.10.2 release build is being used.

## How to Build
1. Download [gsf2wav](https://github.com/jprjr/gsf2wav)
2. go to the gsf2wav folder
3. make sure [lazygsf](https://github.com/jprjr/lazygsf/) is in the lazygsf folder
4. go to the mgba folder in the lazygsf folder.
5. replace the contents of the mgba folder with the source code of the [mgba 0.10.2 release](https://github.com/mgba-emu/mgba/tree/0.10.2).
6. download the source code of this repository
7. place this repository's lazygsf folder in gsf2wav; this will replace the CMakeLists.txt files of lazygsf and mgba with my modified copies.
8. build with cmake
