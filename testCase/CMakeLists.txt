cmake_minimum_required(VERSION 3.20)
project(calc_project)

set(CMAKE_CXX_STANDARD 17)

# its a demo..
set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/out)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/out)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/out)

option(ENABLE_INTERNAL_TESTS "Enable tests for internal API" OFF)
option(ENABLE_INTERNAL_EXPORTS "Enable exporting of internal API functions" OFF)

if(NOT CMAKE_INSTALL_PREFIX)
    message(WARNING "CMAKE_INSTALL_PREFIX is not set, skipping installation")
endif()

add_library(calc SHARED source/Calc.cpp)
target_compile_definitions(calc PRIVATE CALC_EXPORTS)

add_library(calc_interface INTERFACE)
target_include_directories(calc_interface INTERFACE
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/api>
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/source/internalapi>
)

target_include_directories(calc PUBLIC api)
target_include_directories(calc PRIVATE source/internalapi)

if(ENABLE_INTERNAL_TESTS)
    add_definitions(-DCALC_INTERNAL_EXPORTS)
endif()

if(ENABLE_INTERNAL_EXPORTS)
    target_compile_definitions(calc PRIVATE ENABLE_INTERNAL_EXPORTS)
endif()

# TODO: remove google if care..
if(CMAKE_INSTALL_PREFIX)
    install(TARGETS calc calc_interface
        LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
        PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})
    install(FILES api/ICalc.h DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/api)
endif()

add_subdirectory(googletest)

enable_testing()
include(GoogleTest)

add_subdirectory(test)

