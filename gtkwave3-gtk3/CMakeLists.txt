cmake_minimum_required(VERSION 3.4)
project(gtkwave3-gtk3)

option(BUILD_DOC "Build Documentation" ON)
option(BUILD_EXAMPLE "Build Examples" ON)
option(BUILD_MAN "Build Manual" ON)

if (BUILD_DOC)

endif ()

if (BUILD_EXAMPLE)

endif ()

if (BUILD_MAN)

endif ()

add_subdirectory(src)