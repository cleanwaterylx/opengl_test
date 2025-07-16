cmake_minimum_required(VERSION 3.14)
project(OpenGLDemo)

set(CMAKE_CXX_STANDARD 17)

# 添加子模块源码路径
add_subdirectory(3d_party/glad)
add_subdirectory(3d_party/glfw)

# 查找 OpenGL（系统库）
find_package(OpenGL REQUIRED)

# 包含头文件
include_directories(
    3d_party/glad/include
    3d_party/glfw/include
)

# 添加可执行文件
add_executable(OpenGLDemo main.cpp)

# 链接库
target_link_libraries(OpenGLDemo
    glad
    glfw
    ${OPENGL_gl_LIBRARY}
)
