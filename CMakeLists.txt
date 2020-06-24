cmake_minimum_required(VERSION 3.6)
project(sdl2_example)

set(CMAKE_CXX_STANDARD 14)

set(SOURCE_FILES main.cpp glad.c)


if(APPLE)
    # SDL2
    find_package(SDL2 REQUIRED)
    include_directories(${SDL2_INCLUDE_DIRS})

    # sdl2_example executable
    add_executable(sdl2_example ${SOURCE_FILES})
    target_link_libraries(sdl2_example ${SDL2_LIBRARIES})
    target_link_libraries(sdl2_example "-framework Cocoa -framework OpenGL -framework IOKit -framework CoreVideo")
else()
    # SDL2
    find_package(PkgConfig REQUIRED)
    pkg_search_module(SDL2 REQUIRED SDL2)
    include_directories(${SDL2_INCLUDE_DIRS})

    # sdl2_example executable
    add_executable(sdl2_example ${SOURCE_FILES})
    target_link_libraries(sdl2_example ${SDL2_LIBRARY})
endif()