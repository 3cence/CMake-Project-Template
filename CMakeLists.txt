cmake_minimum_required(VERSION 3.29)
# TODO: project( !! PROJECT NAME !! )
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED true)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

execute_process(
    COMMAND ${CMAKE_COMMAND} -E create_symlink
        ${CMAKE_BINARY_DIR}/compile_commands.json
        ${CMAKE_SOURCE_DIR}/compile_commands.json
)

if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Debug)
endif()

set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -Wall -Wextra -Wpedantic -Werror -g -Wno-error=unused-variable -Wno-error=unused-parameter")
set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} -O3")

# TODO: add_executable(${PROJECT_NAME} <source files>)

# In order to find includes, use pkg-config --cflags and pkg-config --libs
target_include_directories(${PROJECT_NAME} PRIVATE ./headers/)
# target_link_libraries(${PROJECT_NAME} <library>)

# target_compile_options(${PROJECT_NAME} PRIVATE <compiler flags for both build type>)
