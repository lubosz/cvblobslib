cmake_minimum_required(VERSION 2.6)
project(cvblobslib)

set(LIBRARY_OUTPUT_PATH ${CMAKE_SOURCE_DIR}/bin)
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_SOURCE_DIR}/bin)

set(SRC_DIR ${CMAKE_SOURCE_DIR}/src)
set(APP_DIR ${CMAKE_SOURCE_DIR}/examples)

#Optimization / Debug
#set(CMAKE_CXX_FLAGS "-O0 -g3") #Debug
set(CMAKE_CXX_FLAGS "-O3") #Optimized

FIND_PACKAGE( OpenCV REQUIRED )

include_directories(
	include
)

#cv blobs lib
set(SOURCES
	${SRC_DIR}/BlobContour.cpp
	${SRC_DIR}/Blob.cpp
	${SRC_DIR}/BlobOperators.cpp
	#${SRC_DIR}/BlobProperties.cpp
	${SRC_DIR}/BlobResult.cpp
	${SRC_DIR}/ComponentLabeling.cpp
)

add_library(cvblobs ${SOURCES})
target_link_libraries(cvblobs ${OpenCV_LIBS})

add_executable(blobTest ${APP_DIR}/blobTest.cpp)
target_link_libraries(blobTest cvblobs)
