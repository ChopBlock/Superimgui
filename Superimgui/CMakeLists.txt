
cmake_minimum_required (VERSION 3.8)
Set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

include_directories(
    ${CMAKE_SOURCE_DIR}/glfw/include/
    ${CMAKE_SOURCE_DIR}/imgui/
    ${CMAKE_SOURCE_DIR}/imgui/backends/
    $ENV{VULKAN_SDK}/Include/
)
#Vulkan_FOUND          - True if Vulkan was found
#Vulkan_INCLUDE_DIRS   - include directories for Vulkan
#Vulkan_LIBRARIES      - link against this library to use Vulkan

message(Vulkan_FOUND:"${Vulkan_FOUND}")
message(Vulkan_INCLUDE_DIRS:"${Vulkan_INCLUDE_DIRS}")
FILE(
GLOB
head_file
    ${CMAKE_SOURCE_DIR}/glfw/include/*h
    ${CMAKE_SOURCE_DIR}/imgui/*h
    ${CMAKE_SOURCE_DIR}/imgui/backends/imgui_impl_vulkan.h
    ${CMAKE_SOURCE_DIR}/imgui/backends/imgui_impl_glfw.h

)
FILE(
GLOB
source_file

${CMAKE_SOURCE_DIR}/imgui/*cpp
${CMAKE_SOURCE_DIR}/imgui/backends/imgui_impl_vulkan.cpp
${CMAKE_SOURCE_DIR}/imgui/backends/imgui_impl_glfw.cpp
)


add_executable (Superimgui Superimgui.cpp
    ${head_file}
    ${source_file}
    )
file(
    GLOB
    vulkanlibs
    $ENV{VULKAN_SDK}/Lib/*lib
    ${CMAKE_SOURCE_DIR}/glfw/lib-vc2019/*lib
    )
target_link_libraries(Superimgui
PUBLIC

${vulkanlibs}
)
