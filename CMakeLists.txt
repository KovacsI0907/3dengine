cmake_minimum_required( VERSION 3.20 )
set (CMAKE_CXX_STANDARD 17)

project( 3dEngine )

find_package( OpenGL REQUIRED )
include_directories( ${OPENGL_INCLUDE_DIRS} )

set( GLFW_BUILD_DOCS OFF CACHE BOOL  "GLFW lib only" )
set( GLFW_INSTALL OFF CACHE BOOL  "GLFW lib only" )

add_subdirectory( external/glfw )

include_directories( external/glad/include )
include_directories( "${GLFW_SOURCE_DIR}/deps" )
set( GLAD_GL "${GLFW_SOURCE_DIR}/deps/glad/gl.h" )

set( 3DENGINE-SRC src/main.cpp external/glad/src/glad.c )

add_executable( 3dEngine ${3DENGINE-SRC} ${GLAD_GL} )
target_link_libraries( 3dEngine ${OPENGL_LIBRARIES} glfw )
