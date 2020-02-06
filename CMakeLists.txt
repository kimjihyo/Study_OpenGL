cmake_minimum_required(VERSION 3.0.0)

project(opengl)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} -Wall -Wextra -Wno-deprecated-declarations")

add_executable(${PROJECT_NAME} src/Main.cpp)

add_subdirectory(deps/glfw-3.3.2)
add_subdirectory(deps/glew-2.1.0/build/cmake)
include_directories(include deps/glfw-3.3.2/include deps/glew-2.1.0/include)

find_package(OpenGL REQUIRED)
target_link_libraries(${PROJECT_NAME} glfw ${GLFW_LIBRARIES} glew OpenGL::GL)