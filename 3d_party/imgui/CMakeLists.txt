cmake_minimum_required(VERSION 3.14)

# 设置include路径
include_directories(
    .
    backends
)

set(IMGUI_SOURCE_FILES
    imgui.cpp
    imgui_demo.cpp
    imgui_draw.cpp
    imgui_tables.cpp
    imgui_widgets.cpp
 
    backends/imgui_impl_glfw.cpp
    backends/imgui_impl_opengl3.cpp
)

add_library(imgui ${IMGUI_SOURCE_FILES})