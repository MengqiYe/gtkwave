add_subdirectory(liblzma)
add_subdirectory(helpers)
add_subdirectory(cocoa)

set(INC ${CMAKE_CURRENT_LIST_DIR}/
        ${CMAKE_SOURCE_DIR}/src/helpers/fst
        ${CMAKE_SOURCE_DIR}/src/helpers
        ${CMAKE_SOURCE_DIR}/src/liblzma
        ${CMAKE_SOURCE_DIR}/src/cocoa
        ${CMAKE_SOURCE_DIR}/src
        ${CMAKE_SOURCE_DIR}/
        ${CMAKE_SOURCE_DIR}/contrib/rtlbrowse
        /usr/include/gtk-3.0
        /usr/include/glib-2.0
        /usr/include/gio-unix-2.0/
        /usr/include/cairo
        /usr/include/pango-1.0
        /usr/include/atk-1.0
        /usr/include/pixman-1
        /usr/include/gdk-pixbuf-2.0
        /usr/include/libpng16
        /usr/include/pango-1.0
        /usr/include/harfbuzz
        /usr/include/pango-1.0
        /usr/include/freetype2
        )
file(GLOB SOURCES RELATIVE ${CMAKE_CURRENT_LIST_DIR}/ ${CMAKE_CURRENT_LIST_DIR}/*.c ${CMAKE_CURRENT_LIST_DIR}/*.h)

find_package(PkgConfig REQUIRED)
pkg_check_modules(GTK3 REQUIRED gtk+-3.0)


add_library(wave ${SOURCES})
target_include_directories(wave PRIVATE ${INC} ${GTK3_INCLUDE_DIRS})
target_link_libraries(wave PRIVATE pthread ${GTK3_LIBRARIES} gtk-x11-2.0 gdk-x11-2.0)

message(STATUS "GTK3_FOUND : ${GTK3_FOUND}")
message(STATUS "GTK3_INCLUDE_DIRS : ${GTK3_INCLUDE_DIRS}")
message(STATUS "GTK3_LIBRARIES : ${GTK3_LIBRARIES}")

include_directories(
        "${CMAKE_SOURCE_DIR}"
        "${CMAKE_SOURCE_DIR}/src"
        "${CMAKE_SOURCE_DIR}/src/liblzma")

add_executable(gtkwave main.c main.h)
target_include_directories(gtkwave PRIVATE ${INC} ${GTK3_INCLUDE_DIRS})
target_link_libraries(gtkwave PRIVATE
        wave fst helpers LzmaLib
        ${GTK3_LIBRARIES}
        pthread m z gtk-x11-2.0 gdk-x11-2.0
        bz2)
