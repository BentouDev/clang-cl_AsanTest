project(App VERSION 0.1 LANGUAGES CXX)

find_package( OpenGL REQUIRED )
include_directories( ${OPENGL_INCLUDE_DIRS} )

if(MSVC)
    SET( CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} /ENTRY:mainCRTStartup" )
endif()
file(GLOB_RECURSE
    APP_SOURCES
    CONFIGURE_DEPENDS
    LIST_DIRECTORIES false
    ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp)

add_executable(App ${APP_SOURCES})

target_include_directories(App 
    PUBLIC
        ${CMAKE_CURRENT_LIST_DIR}/include
        $<BUILD_INTERFACE:${CMAKE_SOURCE_DIR}/Dependencies/GLFW/GLFW/include>
    PRIVATE
        ${CMAKE_CURRENT_LIST_DIR}/src)

target_link_libraries(App
    PUBLIC
        glfw
        Glm
        Imgui
        ${OPENGL_LIBRARIES})

# This makes the project importable from the build directory
export(TARGETS App FILE AppConfig.cmake)