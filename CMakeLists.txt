cmake_minimum_required(VERSION 3.27)
project(moonglfw)
set(CMAKE_CXX_STANDARD 23)

find_package(lua CONFIG REQUIRED)
file(GLOB_RECURSE MOONGLFW_SOURCE CONFIGURE_DEPENDS "src/*.c")
add_library(moonglfw SHARED "${MOONGLFW_SOURCE}")
target_link_directories(moonglfw PUBLIC ./src/include)
target_link_libraries(moonglfw PUBLIC lua::lua)

# Copy moonglfw dynamic library to examples
add_custom_command(TARGET moonglfw POST_BUILD
                   COMMAND ${CMAKE_COMMAND} -E copy
                   $<TARGET_FILE:moonglfw>
                   ${CMAKE_CURRENT_LIST_DIR}/examples)
