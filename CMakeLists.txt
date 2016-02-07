cmake_minimum_required(VERSION 3.1.0)
project(tdpi)

if("${CMAKE_C_COMPILER_ID}" STREQUAL "GNU")
    if(CMAKE_C_COMPILER_VERSION VERSION_LESS 4.9)
        message(WARNING "GCC version must be at least 3.9!")
    endif()
elseif("${CMAKE_C_COMPILER_ID}" STREQUAL "Clang")
    if(CMAKE_C_COMPILER_VERSION VERSION_LESS 3.6)
        message(FATAL_ERROR "Clang version must be at least 3.6!")
    endif()
else()
    message(WARNING "You are using an unsupported compiler!")
endif()

add_library(tdpi ${CMAKE_CURRENT_SOURCE_DIR}/src/tdpi.c)

if(UNIX)
    target_link_libraries(tdpi dl)
endif(UNIX)

target_include_directories(tdpi PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)
