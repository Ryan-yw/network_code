cmake_minimum_required(VERSION 3.12)

project(test)

set(CMAKE_CXX_STANDARD 17)


if(UNIX)
	add_definitions(-DUNIX)
	find_package(aris REQUIRED PATHS /usr/aris)
endif(UNIX)
IF(WIN32)
	find_package(aris REQUIRED PATHS C:/aris/aris-1.5.0)
endif(WIN32)
include_directories(${aris_INCLUDE_DIRS})

file(GLOB SOURCES src/*)
add_executable(test ${SOURCES})
target_link_libraries(test ${aris_LIBRARIES})

