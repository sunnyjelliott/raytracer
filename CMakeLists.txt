cmake_minimum_required(VERSION 3.10)

project(Raytracer VERSION 1.0)

add_definitions(-D_CRT_SECURE_NO_WARNINGS)
add_definitions(-std=c++14)
set_directory_properties(PROPERTIES COMPILE_DEFINITIONS_DEBUG "_DEBUG")

# source files
include_directories("${PROJECT_SOURCE_DIR}/src")
file(GLOB SOURCES "src/*.cpp")

# GLFW
add_subdirectory("${PROJECT_SOURCE_DIR}/submodules/glfw")
include_directories("${PROJECT_SOURCE_DIR}/submodules/glfw/include/GLFW")

# create executable
add_executable(Raytracer ${SOURCES})

# libraries
find_package(Vulkan REQUIRED)
target_link_libraries(Raytracer Vulkan::Vulkan)
target_link_libraries(Raytracer glfw ${GLFW_LIBRARIES})
