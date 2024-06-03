cmake_minimum_required(VERSION 3.10)

# Set the project name
project(MyProject)

# Set the C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Find OpenGL package
find_package(OpenGL REQUIRED)

# Add the include directories
include_directories(
    ${CMAKE_SOURCE_DIR}/include
    ${OPENGL_INCLUDE_DIR}
    ${CMAKE_SOURCE_DIR}/external/glfw/include
    ${CMAKE_SOURCE_DIR}/external/glad/include
)

# Add the GLAD source file
add_library(glad ${CMAKE_SOURCE_DIR}/src/glad.c)

# Add the executable
add_executable(MyProject src/main.cpp)

# Link against GLAD, GLFW, and OpenGL
target_link_libraries(MyProject PRIVATE glad ${CMAKE_SOURCE_DIR}/glfw3.lib ${OPENGL_gl_LIBRARY})
