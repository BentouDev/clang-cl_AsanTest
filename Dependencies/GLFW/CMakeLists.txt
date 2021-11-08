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
    ${CMAKE_CURRENT_LIST_DIR}/GLFW/src/*.c)

add_library(Glfw SHARED ${GLFW_SOURCES})
target_include_directories(Glfw 
    PUBLIC
	    ${CMAKE_CURRENT_LIST_DIR}/GLFW/include
    PRIVATE
        ${CMAKE_CURRENT_LIST_DIR}/GLFW/src)

# This makes the project importable from the build directory
export(TARGETS Glfw FILE GlfwConfig.cmake)