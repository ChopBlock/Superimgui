# CMakeList.txt: Superimgui 的 CMake 项目，在此处包括源代码并定义
# 项目特定的逻辑。
#
cmake_minimum_required (VERSION 3.8)
Set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include_directories(
    glfw/include/
    imgui/
    imgui/backends/
)
FILE(
GLOB
head_file
glfw/include/*h
    imgui/*h
    imgui/backends/*h
)

# 将源代码添加到此项目的可执行文件。
add_executable (Superimgui Superimgui.cpp Superimgui.h ${head_file})

# TODO: 如有需要，请添加测试并安装目标。
