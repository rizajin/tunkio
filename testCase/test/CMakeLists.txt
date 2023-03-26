# Create a test executable linked with the main calc library and Google Test
add_executable(calc_tests
    api/CalcApiTest.cpp
    internal/CalcInternalTest.cpp
)

# Link the test target to the calc library and the calc_interface target
target_link_libraries(calc_tests PRIVATE calc calc_interface gtest gtest_main)
if(ENABLE_INTERNAL_TESTS)
    target_compile_definitions(calc_tests PRIVATE ENABLE_INTERNAL_EXPORTS)
endif()

# Add include directories for the test target
target_include_directories(calc_tests PRIVATE
    ${CMAKE_SOURCE_DIR}/api
    ${CMAKE_SOURCE_DIR}/source/internalapi
)

# Add the test to the CTest test runner
gtest_discover_tests(calc_tests)
