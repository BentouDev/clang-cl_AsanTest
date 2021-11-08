project(App VERSION 0.1 LANGUAGES CXX)

# file(GLOB_RECURSE
#     APP_HEADERS
#     CONFIGURE_DEPENDS
#     LIST_DIRECTORIES false
#     ${CMAKE_CURRENT_SOURCE_DIR}/*.h)

file(GLOB_RECURSE
    APP_SOURCES
    CONFIGURE_DEPENDS
    LIST_DIRECTORIES false
    ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp)

add_executable(App ${APP_SOURCES})

target_include_directories(App 
    PUBLIC
        ${CMAKE_CURRENT_LIST_DIR}/include
    PRIVATE
        ${CMAKE_CURRENT_LIST_DIR}/src)

target_link_libraries(App
    PUBLIC
        Glfw
        Glm)

# This makes the project importable from the build directory
export(TARGETS App FILE AppConfig.cmake)