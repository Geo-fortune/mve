cmake_minimum_required(VERSION 3.5)
project(mve CXX)

# library 
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/src)

# add libs
add_subdirectory(src)
add_subdirectory(apps)