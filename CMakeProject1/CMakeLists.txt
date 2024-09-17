# CMakeList.txt : Top-level CMake project file, do global configuration
# and include sub-projects here.
#
cmake_minimum_required (VERSION 3.8)



# Get the current source directory (or any directory)
set(CURRENT_DIR ${CMAKE_SOURCE_DIR})

# Get the parent directory of CURRENT_DIR
get_filename_component(PARENT_DIR ${CURRENT_DIR} DIRECTORY)

get_filename_component(PARENT_PARENT_DIR ${PARENT_DIR} DIRECTORY)

set(CMAKE_PREFIX_PATH "${PARENT_PARENT_DIR}/vcpkg/installed/x64-windows")

set(CMAKE_TOOLCHAIN_FILE "${PARENT_PARENT_DIR}/vcpkg/scripts/buildsystems/vcpkg.cmake" CACHE STRING "Vcpkg toolchain file")

project ("CMakeProject1")

set(CMAKE_CXX_STANDARD 20)

find_package(glm CONFIG REQUIRED)

add_executable(CMakeProject1 CMakeProject1/CMakeProject1.cpp)

target_link_libraries(CMakeProject1 PRIVATE glm::glm)
