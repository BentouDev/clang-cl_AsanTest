cmake_minimum_required(VERSION 3.14 FATAL_ERROR)
project(CUBE_MSVC_2022 VERSION 1.0 LANGUAGES CXX C)

add_subdirectory(Dependencies/GLFW)
add_subdirectory(Dependencies/GLM)
add_subdirectory(Dependencies/IMGUI)
add_subdirectory(App)
