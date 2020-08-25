set(INC ${CMAKE_CURRENT_LIST_DIR}/../ ${CMAKE_CURRENT_LIST_DIR})

add_library(LzmaLib LzmaLib.c LzmaLib.h)
target_include_directories(LzmaLib PRIVATE ${INC})