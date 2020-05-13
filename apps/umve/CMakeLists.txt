
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -msse4.1")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -msse4.1")
set(CMAKE_INCLUDE_CURRENT_DIR ON)


file(GLOB_RECURSE HDR_FILES ${CMAKE_CURRENT_SOURCE_DIR}/*.h)
file(GLOB_RECURSE SRC_FILES ${CMAKE_CURRENT_SOURCE_DIR}/*.cc ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp )


if (POLICY CMP0072)
  set(OpenGL_GL_PREFERENCE LEGACY)
endif()

find_package(OpenGL REQUIRED)
include_directories(${OpenGL_INCLUDE_DIR})

find_package(Qt5 COMPONENTS Widgets Core Gui OpenGL REQUIRED)
# SET(QT_USE_QTOPENGL TRUE)
set(CMAKE_AUTORCC ON)
# set(CMAKE_AUTOMOC ON)

# resource file
qt5_add_resources(RCC_WRAP ${CMAKE_CURRENT_SOURCE_DIR}/umve.qrc)
#生成moc文件
qt5_wrap_cpp(MOC_WRAP ${HDR_FILES})

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
add_executable(umve ${SRC_FILES} ${MOC_WRAP} ${RCC_WRAP})
target_link_libraries(umve mve_dmrecon 
                           mve
                           mve_util 
                           mve_ogl 
                           png 
                           jpeg 
                           tiff 
                           Qt5::Widgets 
                           Qt5::Core 
                           Qt5::Gui
                           Qt5::OpenGL
                           ${OPENGL_LIBRARY}
                           )
                
#copy shaders to "bin" dir
set(SHADER_DIR ${CMAKE_CURRENT_LIST_DIR}/shaders)
message(STATUS "shader: ${SHADER_DIR}")
install(DIRECTORY ${SHADER_DIR} DESTINATION ${EXECUTABLE_OUTPUT_PATH}/shaders/)