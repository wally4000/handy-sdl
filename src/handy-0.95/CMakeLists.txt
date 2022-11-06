add_compile_definitions(SDL_PATCH ANSI_GCC)
include_directories(${PROJECT_SOURCE_DIR}/zlib-113)
add_library(core cart.cpp memmap.cpp mikie.cpp ram.cpp rom.cpp susie.cpp system.cpp)

