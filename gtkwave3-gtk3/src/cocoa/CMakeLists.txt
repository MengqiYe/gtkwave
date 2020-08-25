set(INC ${CMAKE_CURRENT_LIST_DIR}/
        ${CMAKE_SOURCE_DIR}/src/helpers/fst
        ${CMAKE_SOURCE_DIR}/src/liblzma
        ${CMAKE_SOURCE_DIR}/src
        ${CMAKE_SOURCE_DIR}/
        ${CMAKE_CURRENT_LIST_DIR}/../../contrib/rtlbrowse)
file(GLOB SOURCES RELATIVE ${CMAKE_CURRENT_LIST_DIR}/ ${CMAKE_CURRENT_LIST_DIR}/*.c ${CMAKE_CURRENT_LIST_DIR}/*.h)


message(STATUS "CMAKE_MODULE_PATH : ${CMAKE_MODULE_PATH}")

find_package(PkgConfig REQUIRED)
pkg_check_modules(GTK3 REQUIRED gtk+-3.0)

add_library(libcocoa ${SOURCES})
target_include_directories(libcocoa PRIVATE ${INC} ${GTK3_INCLUDE_DIRS})
target_link_libraries(libcocoa PRIVATE ${GTK3_LIBRARIES})

message(STATUS "GTK3_FOUND : ${GTK3_FOUND}")
message(STATUS "GTK3_INCLUDE_DIRS : ${GTK3_INCLUDE_DIRS}")
message(STATUS "GTK3_LIBRARIES : ${GTK3_LIBRARIES}")