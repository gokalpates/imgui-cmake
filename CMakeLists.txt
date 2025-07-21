cmake_minimum_required(VERSION 3.20)

project(imgui-cmake VERSION 0.0.1)

add_library(imgui-static-wrapper STATIC
    include/ImguiWrapper.h

    "thirdparty/imgui/imconfig.h"
    "thirdparty/imgui/imgui.h"
    "thirdparty/imgui/backends/imgui_impl_glfw.h"
    "thirdparty/imgui/backends/imgui_impl_vulkan.h"
    "thirdparty/imgui/imgui_internal.h"
    "thirdparty/imgui/imstb_rectpack.h"
    "thirdparty/imgui/imstb_textedit.h"
    "thirdparty/imgui/imstb_truetype.h"

    "thirdparty/imgui/imgui.cpp"
    "thirdparty/imgui/imgui_demo.cpp"
    "thirdparty/imgui/imgui_draw.cpp"
    "thirdparty/imgui/backends/imgui_impl_glfw.cpp"
    "thirdparty/imgui/backends/imgui_impl_vulkan.cpp"
    "thirdparty/imgui/imgui_tables.cpp"
    "thirdparty/imgui/imgui_widgets.cpp"
)

target_compile_definitions(imgui-static-wrapper PUBLIC IMGUI_IMPL_VULKAN_USE_VOLK)

target_include_directories(imgui-static-wrapper PUBLIC 
    ${CMAKE_CURRENT_SOURCE_DIR}/include
    ${CMAKE_CURRENT_SOURCE_DIR}/thirdparty/imgui
    ${CMAKE_CURRENT_SOURCE_DIR}/thirdparty/imgui/backends
)

target_link_libraries(imgui-static-wrapper PUBLIC volk glfw)