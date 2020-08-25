set(INC ${CMAKE_SOURCE_DIR}/src/helpers/fst
        ${CMAKE_SOURCE_DIR}/src/helpers/
        ${CMAKE_SOURCE_DIR}/
        )
file(GLOB SOURCES RELATIVE ${CMAKE_CURRENT_LIST_DIR}/ ${CMAKE_CURRENT_LIST_DIR}/*.c)

message(STATUS "INC : ${INC}")
message(STATUS "SOURCES : ${SOURCES}")

add_library(fst ${SOURCES})
target_include_directories(fst PRIVATE ${INC})