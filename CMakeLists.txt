cmake_minimum_required(VERSION 2.8.12)

project(opengl-gui)

add_definitions("-std=c++11")

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

# CONFIG option is important so that CMake doesnt search for modules into the default modules directory

find_package(imgui CONFIG)

find_package(OpenGL REQUIRED)

find_package(glfw3 CONFIG)
find_package(GLEW CONFIG)

#find_package(SDL2 REQUIRED)
#include_directories(${SDL2_INCLUDE_DIRS})

add_executable( opengl-gui
                main.cpp
                imgui_impl_glfw.cpp
#                imgui_impl_opengl3.cpp
                imgui_impl_glfw.h
#                imgui_impl_opengl3.h
                imgui_impl_opengl2.h
                imgui_impl_opengl2.cpp
            )


target_include_directories(opengl-gui PRIVATE ${OPENGL_INCLUDE_DIR})

target_link_libraries(opengl-gui ${OPENGL_LIBRARIES} glfw imgui)

install(TARGETS opengl-gui DESTINATION bin)
set_target_properties(opengl-gui PROPERTIES DEBUG_POSTFIX _d)





#target_compile_definitions(main PUBLIC IMGUI_IMPL_OPENGL_LOADER_GLEW)

#target_link_libraries(main glfw imgui)
#target_link_libraries(main imgui glfw3 GLEW ${CONAN_LIBS})



#target_link_libraries(${PROJECT_NAME} -ldl)
