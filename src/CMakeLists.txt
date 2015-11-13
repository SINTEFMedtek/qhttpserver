###########################################################
# library: qhttpserver
###########################################################

find_package(Qt5Network REQUIRED)
#find_package(Qt5Gui REQUIRED)
set(HTTP_PARSER_DIR "${PROJECT_SOURCE_DIR}/http-parser")

set(SOURCES
    qhttpconnection.cpp
    qhttprequest.cpp
    qhttpresponse.cpp
    qhttpserver.cpp
    qhttpserverapi.h
    qhttpserverfwd.h
    ${HTTP_PARSER_DIR}/http_parser.h
    ${HTTP_PARSER_DIR}/http_parser.c
    )
qt5_wrap_cpp(SOURCES
    qhttpconnection.h
    qhttprequest.h
    qhttpresponse.h
    qhttpserver.h
    )

set(PUBLIC_LINK_LIBRARIES
    )
set(PUBLIC_INCLUDE_DIRECTORIES
    ${CMAKE_CURRENT_SOURCE_DIR}
    )


add_library (qhttpserver ${SOURCES})
add_definitions(-DQHTTPSERVER_EXPORT)

target_include_directories (qhttpserver
    PUBLIC
    ${PUBLIC_INCLUDE_DIRECTORIES}
    PRIVATE
    ${HTTP_PARSER_DIR}
    )

target_link_libraries(qhttpserver
    PUBLIC
    ${PUBLIC_LINK_LIBRARIES}
    PRIVATE
    Qt5::Network
    )
    
    
    
install(TARGETS qhttpserver EXPORT qhttpserverTargets
  LIBRARY DESTINATION lib
  ARCHIVE DESTINATION lib
  RUNTIME DESTINATION bin
  INCLUDES DESTINATION include
)
  
#set(ConfigPackageLocation lib/cmake/ClimbingStats)
#install(EXPORT ClimbingStatsTargets
#  FILE
#    ClimbingStatsTargets.cmake
#  DESTINATION
#    ${ConfigPackageLocation}
#)