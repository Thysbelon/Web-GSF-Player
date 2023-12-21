# for gsf2wav

cmake_minimum_required(VERSION 3.1)

project(gsf2wav)

find_package(ZLIB REQUIRED)

add_subdirectory(lazygsf)
add_library(psflib STATIC psflib/psflib.c psflib/psf2fs.c)
target_link_libraries(psflib PRIVATE ZLIB::ZLIB)

if(EMSCRIPTEN)
	set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wno-error=incompatible-pointer-types -Wno-error=incompatible-function-pointer-types") # There's a pointer types warning when building gsf2wav.o with gcc, but it's an error in Emscripten. attempting to remove error. this may not work
	#set(LINK_FLAGS "${LINK_FLAGS} -sEXPORTED_RUNTIME_METHODS=FS -sMODULARIZE -s 'EXPORT_NAME=\"WebSPCplayer\"'")
	#set(LINK_FLAGS "${LINK_FLAGS} -sEXPORTED_RUNTIME_METHODS=FS -sMODULARIZE -s EXPORT_NAME=WebSPCplayer")
	add_link_options(-sEXPORTED_RUNTIME_METHODS=FS -sMODULARIZE -s EXPORT_NAME=WebGSFplayer)
endif()

add_executable(gsf2wav gsf2wav.c)
target_include_directories(gsf2wav PRIVATE psflib)
target_link_libraries(gsf2wav PRIVATE lazygsf psflib)
