
#cmake acquire the dir name

set (MODEL_NAME ogl)
include_directories("/usr/include")

if (POLICY CMP0072)
  set(OpenGL_GL_PREFERENCE LEGACY)
endif()

find_package(OpenGL REQUIRED)
include_directories(${OpenGL_INCLUDE_DIR})

message(STATUS "opengl : ${OPENGL_INCLUDE_DIR}")
message(STATUS "opengl : ${OPENGL_LIBRARY}")

# file
file(GLOB_RECURSE HDR_FILES ${CMAKE_CURRENT_LIST_DIR}/*.h)
file(GLOB_RECURSE SRC_FILES ${CMAKE_CURRENT_LIST_DIR}/*.cpp ${CMAKE_CURRENT_LIST_DIR}/*.cc)

set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
add_library(mve_ogl STATIC ${SRC_FILES} ${HDR_FILES})
target_link_libraries(mve_ogl ${OPENGL_LIBRARY})