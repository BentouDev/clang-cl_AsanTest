project(GLFW VERSION 0.1 LANGUAGES CXX)

# file(GLOB_RECURSE
#     GLFW_HEADERS
#     CONFIGURE_DEPENDS
#     LIST_DIRECTORIES false
#     ${CMAKE_CURRENT_SOURCE_DIR}/*.h)

file(GLOB_RECURSE
    GLFW_SOURCES
    CONFIGURE_DEPENDS
    LIST_DIRECTORIES false
    ${CMAKE_CURRENT_SOURCE_DIR}/src/*.c
    ${CMAKE_CURRENT_SOURCE_DIR}/src/*.cxx
    ${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp)

add_library(Glfw SHARED ${GLFW_SOURCES})
target_include_directories(Glfw 
    PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
    PRIVATE
        src)

# This makes the project importable from the build directory
export(TARGETS Glfw FILE GlfwConfig.cmake)