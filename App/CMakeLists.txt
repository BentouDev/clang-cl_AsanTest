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

add_executable(App WIN32
    ${APP_SOURCES}
    ${CMAKE_SOURCE_DIR}/Dependencies/IMGUI/IMGUI/backends/imgui_impl_glfw.cpp)

## ASAN
target_compile_options(App PRIVATE -fsanitize=address) # /MD will be used implicitly
target_link_directories(App PRIVATE "$ENV{PROGRAMFILES}/Microsoft Visual Studio/2022/Community/VC/Tools/Llvm/x64/lib/clang/12.0.0/lib/windows")
target_link_libraries(App PRIVATE clang_rt.asan_dynamic-x86_64 clang_rt.asan_dynamic_runtime_thunk-x86_64)
target_link_options(App PRIVATE /wholearchive:clang_rt.asan_dynamic_runtime_thunk-x86_64.lib /DEBUG)

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