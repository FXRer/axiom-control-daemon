CMAKE_MINIMUM_REQUIRED(VERSION 3.10)
PROJECT(DaemonCLI)

#SET(CMAKE_GENERATOR "Unix Makefiles" CACHE INTERNAL "" FORCE)
#SET(CMAKE_VERBOSE_MAKEFILE ON)

FILE(GLOB SOURCE_FILES "*.cpp" "*.h"
                       "${CMAKE_SOURCE_DIR}/API_WS/MessageHandler.cpp" "${CMAKE_SOURCE_DIR}/API_WS/MessageHandler.h")
#    "Adapter/*.cpp" "Adapter/*.h"

#    "Connection/*.cpp" "Connection/*.h"
#    "Schema/*.cpp"RESTServer "Schema/*.h" "Schema/*.fbs")

#ADD_CUSTOM_TARGET(flatc_gen 
#                    COMMAND ${FLATC} --scoped-enums --no-prefix --cpp ${PROJECT_SOURCE_DIR}/Schema/axiom_daemon.fbs
#                    WORKING_DIRECTORY ${PROJECT_SOURCE_DIR}/Schema/
#                    COMMENT "Running PRE_BUILD action" DEPENDS flatc)

ADD_EXECUTABLE(${PROJECT_NAME} ${SOURCE_FILES})

#ExternalProject_Get_Property(flatbuffers_project SOURCE_DIR)
#MESSAGE(STATUS "flatbuffers source dir: ${SOURCE_DIR}")
#TARGET_INCLUDE_DIRECTORIES(${PROJECT_NAME} PUBLIC ${SOURCE_DIR}/include)

TARGET_INCLUDE_DIRECTORIES(${PROJECT_NAME} PUBLIC ${CMAKE_BINARY_DIR}/src/ ../3rdParty/)

#ExternalProject_Get_Property(uWebSockets SOURCE_DIR)

#MESSAGE(STATUS "uWebSockets INC DIR: ${INCLUDE_DIRECTORIES}")

ADD_DEPENDENCIES(${PROJECT_NAME} flatbuffers_project flatc_cpp_gen)
#TARGET_LINK_LIBRARIES(${PROJECT_NAME} ${SOURCE_DIR}/libuWS.so ssl z)
