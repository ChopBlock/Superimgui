
cmake_minimum_required (VERSION 3.8)
Set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include_directories(
    ${CMAKE_SOURCE_DIR}/glfw/include/
    ${CMAKE_SOURCE_DIR}/imgui/
    ${CMAKE_SOURCE_DIR}/imgui/backends/
    C:/VulkanSDK/1.2.198.1/Include/
)
message(sourcedir: "${CMAKE_SOURCE_DIR}")
FILE(
GLOB
head_file
${CMAKE_SOURCE_DIR}/glfw/include/*h
    ${CMAKE_SOURCE_DIR}/imgui/*h
    ${CMAKE_SOURCE_DIR}/imgui/backends/imgui_impl_vulkan.h
    ${CMAKE_SOURCE_DIR}/imgui/backends/imgui_impl_glfw.h
    C:/VulkanSDK/1.2.198.1/Include/*h
)
FILE(
GLOB
source_file

${CMAKE_SOURCE_DIR}/imgui/*cpp
${CMAKE_SOURCE_DIR}/imgui/backends/imgui_impl_vulkan.cpp
${CMAKE_SOURCE_DIR}/imgui/backends/imgui_impl_glfw.cpp
)


add_executable (Superimgui Superimgui.cpp  ${head_file} ${source_file})

target_link_libraries(Superimgui
PUBLIC
${CMAKE_SOURCE_DIR}/glfw/lib-vc2019/glfw3.lib
)
