include(FetchContent)
FetchContent_Declare(
    googletest
    URL https://github.com/google/googletest/archive/refs/tags/v1.15.2.zip
    DOWNLOAD_EXTRACT_TIMESTAMP TRUE
)
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)   # required on Windows/MSVC
set(INSTALL_GTEST OFF CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(googletest)

add_executable(app_core_tests
    vehicle_state_test.cpp
)
target_link_libraries(app_core_tests PRIVATE app_core GTest::gtest_main GTest::gmock)

include(GoogleTest)
gtest_discover_tests(app_core_tests)