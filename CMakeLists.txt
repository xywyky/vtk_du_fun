cmake_minimum_required(VERSION 2.8)
 


set(CMAKE_OSX_DEPLOYMENT_TARGET "10.15" CACHE STRING "Minimum OS X deployment version")



PROJECT(vtktp)



IF(APPLE)

SET( OperatingSystem "Mac os X")
set (MY_MESHES_PATH  /Users/emmanuelmelin/shared_folders/data_VTK)


find_package(VTK 9 REQUIRED)

ENDIF (APPLE)

IF(${CMAKE_SYSTEM_NAME} MATCHES "Linux")

SET(OperatingSystem "Linux")

set (MY_MESHES_PATH  /tp)

find_package(VTK)
include(${VTK_USE_FILE})

ENDIF(${CMAKE_SYSTEM_NAME} MATCHES "Linux")


MESSAGE(WARNING "System detected:${OperatingSystem}" )
MESSAGE(WARNING "Path to data:${MY_MESHES_PATH}" )


configure_file (
  "${PROJECT_SOURCE_DIR}/config.h.in"
  "${PROJECT_BINARY_DIR}/config.h"
  )
 

file(GLOB SRC_LIST ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp )

include_directories("${PROJECT_BINARY_DIR}")

add_executable(${PROJECT_NAME} ${SRC_LIST})

 
target_link_libraries(${PROJECT_NAME} ${VTK_LIBRARIES})


enable_testing()
add_test(SimpleTest ${PROJECT_NAME})
add_custom_target(check COMMAND ${CMAKE_CTEST_COMMAND}
                  DEPENDS ${PROJECT_NAME})
