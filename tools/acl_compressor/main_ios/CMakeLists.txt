cmake_minimum_required (VERSION 3.2)
project(acl_compressor)

# iOS cmake toolchain does not support CMAKE_CXX_STANDARD
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

# Force enable debug symbols
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g")

# Enable optimizations in Release
set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} -O3")

set(MACOSX_BUNDLE_EXECUTABLE_NAME ${PROJECT_NAME})
set(MACOSX_BUNDLE_INFO_STRING "com.acl.acl-compressor")
set(MACOSX_BUNDLE_GUI_IDENTIFIER "com.acl.acl-compressor")
set(MACOSX_BUNDLE_BUNDLE_NAME "acl-compressor")

include_directories("${PROJECT_SOURCE_DIR}/../../../includes")
include_directories("${PROJECT_SOURCE_DIR}/../../../external/sjson-cpp-0.4.0/includes")
include_directories("${PROJECT_SOURCE_DIR}/../includes")

# Grab all of our common source files
file(GLOB_RECURSE ALL_COMMON_SOURCE_FILES LIST_DIRECTORIES false
	${PROJECT_SOURCE_DIR}/../includes/*.h
	${PROJECT_SOURCE_DIR}/../sources/*.cpp)

create_source_groups("${ALL_COMMON_SOURCE_FILES}" ${PROJECT_SOURCE_DIR}/..)

# Grab all of our main source files
file(GLOB_RECURSE ALL_MAIN_SOURCE_FILES LIST_DIRECTORIES false
	${PROJECT_SOURCE_DIR}/*.cpp)

create_source_groups("${ALL_MAIN_SOURCE_FILES}" ${PROJECT_SOURCE_DIR})

add_executable(${PROJECT_NAME} MACOSX_BUNDLE ${ALL_COMMON_SOURCE_FILES} ${ALL_MAIN_SOURCE_FILES})
