###########################################################
project(qhttpserver)
###########################################################

cmake_minimum_required(VERSION 2.8.12.2)

if(POLICY policy-id)
    cmake_policy(SET CMP0042 NEW)
endif()

set(BUILD_SHARED_LIBS ON CACHE BOOL "build shared or static libs")
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "${PROJECT_BINARY_DIR}/bin")
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${PROJECT_BINARY_DIR}/bin")
    
add_subdirectory(src)


#export(EXPORT qhttpserverTargets
export(TARGETS qhttpserver
  FILE "${CMAKE_CURRENT_BINARY_DIR}/qhttpserverTargets.cmake"
)
configure_file(qhttpserverConfig.cmake.in
  qhttpserverConfig.cmake
)
