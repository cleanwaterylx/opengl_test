cmake_minimum_required(VERSION 3.14)
project(OpenGLDemo)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_BUILD_TYPE Debug)

# 添加子模块源码路径
add_subdirectory(3d_party/glad)
add_subdirectory(3d_party/glfw)
add_subdirectory(3d_party/glm)

set(IMGUI_DIR ${CMAKE_CURRENT_SOURCE_DIR}/3d_party/imgui)
set(IMGUI_SOURCE_FILES
    ${IMGUI_DIR}/imgui.cpp
    ${IMGUI_DIR}/imgui_demo.cpp
    ${IMGUI_DIR}/imgui_draw.cpp
    ${IMGUI_DIR}/imgui_tables.cpp
    ${IMGUI_DIR}/imgui_widgets.cpp
 
    ${IMGUI_DIR}/backends/imgui_impl_glfw.cpp
    ${IMGUI_DIR}/backends/imgui_impl_opengl3.cpp
)
add_library(imgui ${IMGUI_SOURCE_FILES})

# 包含头文件
include_directories(
    3d_party/glad/include
    3d_party/glfw/include
    3d_party/imgui
    3d_party/imgui/backends
)

file(GLOB_RECURSE sources "source/*.cpp" "source/*.h")

# 添加可执行文件
add_executable(OpenGLDemo ${sources})

# 链接库
target_link_libraries(OpenGLDemo
    glad
    glfw
    glm::glm
    imgui
)
