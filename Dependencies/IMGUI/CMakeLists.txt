project(IMGUI VERSION 0.1 LANGUAGES CXX)

set(IMGUI_SRC_DIR ${CMAKE_CURRENT_LIST_DIR}/IMGUI)

add_library(Imgui STATIC
	${IMGUI_SRC_DIR}/imgui.cpp
	${IMGUI_SRC_DIR}/imgui_widgets.cpp
	${IMGUI_SRC_DIR}/imgui_tables.cpp 
	${IMGUI_SRC_DIR}/imgui_draw.cpp 
	${IMGUI_SRC_DIR}/imgui_demo.cpp 
	${IMGUI_SRC_DIR}/backends/imgui_impl_opengl3.cpp)

target_include_directories(Imgui
    PUBLIC
	    ${CMAKE_CURRENT_LIST_DIR}/IMGUI
		${CMAKE_CURRENT_LIST_DIR}/IMGUI/backends)

# This makes the project importable from the build directory
export(TARGETS Imgui FILE ImguiConfig.cmake)