project(GLM VERSION 0.1 LANGUAGES CXX)

add_library(Glm INTERFACE)
target_include_directories(Glm
    INTERFACE
        ${CMAKE_CURRENT_LIST_DIR}/GLM)

# This makes the project importable from the build directory
export(TARGETS Glm FILE GlmConfig.cmake)