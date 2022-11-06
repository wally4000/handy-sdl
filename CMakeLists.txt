project(handy-sdl)

cmake_minimum_required(VERSION 3.14)
add_subdirectory(src)


 

add_executable(handy-sdl src/handy_sdl_main.cpp)
include_directories(handy-sdl BEFORE src src/handy-0.95 src/sdlemu)
target_link_libraries(handy-sdl core handy-0.95 zlib gui sdlemu)