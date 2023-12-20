# Web-GSF-Player
Work in progress. Will play GSF files in the browser.

mgba CMakeLists.txt modifications were copied from [@jprjr's fork](https://github.com/mgba-emu/mgba/pull/2065).
These modifications allow libmgba.a to be compiled with threads disabled and MINIMAL_CORE set to 2.

The lazygsf CMakeLists.txt modifications call mgba's CMakeLists.txt instead of manually including sources; the goal of this modification was to make it easier to update mgba to the latest version.

Right now, the mgba 0.10.2 release build is being used.

(files will be added later)
