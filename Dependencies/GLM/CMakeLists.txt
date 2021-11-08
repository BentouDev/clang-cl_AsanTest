project(GLM VERSION 0.1 LANGUAGES CXX)

add_library(GLM INTERFACE)
target_include_directories(Glm
    INTERFACE
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>)

# This makes the project importable from the build directory
export(TARGETS Glm FILE GlmConfig.cmake)