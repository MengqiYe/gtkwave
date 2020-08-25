set(INC ${CMAKE_CURRENT_LIST_DIR}/
        ${CMAKE_SOURCE_DIR}/src/helpers/fst
        ${CMAKE_SOURCE_DIR}/src/liblzma
        ${CMAKE_SOURCE_DIR}/src
        ${CMAKE_SOURCE_DIR}/
        ${CMAKE_CURRENT_LIST_DIR}/../../contrib/rtlbrowse)
file(GLOB SOURCES RELATIVE ${CMAKE_CURRENT_LIST_DIR}/ ${CMAKE_CURRENT_LIST_DIR}/*.c ${CMAKE_CURRENT_LIST_DIR}/*.h)

message(STATUS "INC : ${INC}")
message(STATUS "SOURCES : ${SOURCES}")

include_directories(
        "${CMAKE_SOURCE_DIR}"
        "${CMAKE_SOURCE_DIR}/src"
        "${CMAKE_SOURCE_DIR}/src/liblzma")

add_library(helpers ${SOURCES})
target_include_directories(LzmaLib PUBLIC ${INC})

add_subdirectory(fst)