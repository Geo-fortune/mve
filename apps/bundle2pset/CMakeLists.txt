
file(GLOB_RECURSE HDR_FILES ${CMAKE_CURRENT_LIST_DIR}/*.h)
file(GLOB_RECURSE SRC_FILES ${CMAKE_CURRENT_LIST_DIR}/*.cpp ${CMAKE_CURRENT_LIST_DIR}/*.cc)

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
# add_library(bundle2pset STATIC ${SRC_FILES})
add_executable(bundle2pset ${SRC_FILES})
target_link_libraries(bundle2pset  mve mve_util png tiff jpeg)