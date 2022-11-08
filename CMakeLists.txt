project(handy-sdl)

## Requires minizip, zlib SDL 1.2

find_package(SDL)
find_package(zlib)
find_package(OpenGL)
cmake_minimum_required(VERSION 3.14)


message(${SDL_LIBRARIES})

add_compile_definitions(SDL_PATCH ANSI_GCC )
add_library(Core src/Core/cart.cpp src/Core/memmap.cpp src/Core/mikie.cpp src/Core/ram.cpp src/Core/rom.cpp src/Core/susie.cpp src/Core/system.cpp)
add_library(sdlemu  src/sdlemu/handy_sdl_graphics.cpp src/sdlemu/handy_sdl_handling.cpp src/sdlemu/handy_sdl_sound.cpp src/sdlemu/sdlemu_filter.cpp src/sdlemu/sdlemu_opengl.c src/sdlemu/sdlemu_overlay.c src/sdlemu/sdlemu_video.c )
add_library(gui src/gui/font.cpp src/gui/gui.cpp)
add_library(zlib src/zlib-113/unzip.c)



add_executable(handy-sdl src/handy_sdl_main.cpp)
include_directories( src src/Core src/sdlemu ${ZLIB_INCLUDE_DIRS} ${SDL_INCLUDE_DIRS} src/zlib-113)
target_link_libraries(handy-sdl ${OPENGL_LIBRARIES} ${SDL_LIBRARIES} ${ZLIB_LIBRARIES} ${MINIZIP_LIBRARIES} Core sdlemu zlib gui   )
