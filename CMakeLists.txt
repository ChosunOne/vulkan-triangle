cmake_minimum_required(VERSION 3.16)
project(triangle)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_LINK_EXECUTABLE "${CMAKE_CXX_LINK_EXECUTABLE} -ldl")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++17 -pthread")
set(GLFW_VULKAN_STATIC true)

find_package(PkgConfig REQUIRED)
pkg_search_module(GLFW REQUIRED glfw3)
include_directories(${GLFW_INCLUDE_DIRS})

find_package(Vulkan REQUIRED)

find_library(STB_LIB NAMES stb_image.h PATHS $ENV{STB_INCLUDE_PATH})
include_directories(${STB_LIB})

add_executable(triangle src/main.cpp)
target_link_libraries(triangle glfw3 ${GLFW_STATIC_LIBRARIES} Vulkan::Vulkan)