file(GLOB_RECURSE HDR_FILES ${CMAKE_CURRENT_LIST_DIR}/*.h)
file(GLOB_RECURSE SRC_FILES ${CMAKE_CURRENT_LIST_DIR}/*.cpp ${CMAKE_CURRENT_LIST_DIR}/*.cc)

set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
add_executable(sfmrecon ${SRC_FILES})
target_link_libraries(sfmrecon mve_sfm
                               mve 
                               mve_util 
                               png 
                               tiff 
                               jpeg 
                               pthread)