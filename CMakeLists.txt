cmake_minimum_required(VERSION 3.7)

project(fc14play C)

find_package(SDL2 REQUIRED)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${fc14play_SOURCE_DIR}/fc14play/release/other/")

file(GLOB fc14play_SRC
    "${fc14play_SOURCE_DIR}/audiodrivers/sdl/*.c"
    "${fc14play_SOURCE_DIR}/*.c"
    "${fc14play_SOURCE_DIR}/fc14play/src/*.c"
)

add_executable(fc14play ${fc14play_SRC})

target_include_directories(fc14play SYSTEM
    PRIVATE ${SDL2_INCLUDE_DIRS})

if("${SDL2_LIBRARIES}" STREQUAL "")
    message(WARNING "SDL2_LIBRARIES wasn't set, manually setting to SDL2::SDL2")
    set(SDL2_LIBRARIES "SDL2::SDL2")
endif()

target_link_libraries(fc14play
    PRIVATE m pthread ${SDL2_LIBRARIES})

target_compile_definitions(fc14play
    PRIVATE AUDIODRIVER_SDL)

install(TARGETS fc14play
    RUNTIME DESTINATION bin)
