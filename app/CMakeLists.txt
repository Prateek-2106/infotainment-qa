add_library(app_core
    core/src/vehicle_state.cpp
)
target_include_directories(app_core PUBLIC core/include)

if(MSVC)
    target_compile_options(app_core PRIVATE /W4 /permissive-)
else()
    target_compile_options(app_core PRIVATE -Wall -Wextra -Wpedantic)
endif()

add_subdirectory(tests)