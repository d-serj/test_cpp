cmake_minimum_required (VERSION 3.0)
project (test LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 11)

# configure compiler flags
set(flags "-Wall -Werror")
option(use_flags "Do you want to use an another library?" ON)
if (use_flags)
	set(${CMAKE_CXX_FLAGS} ${flags})
	message(STATUS "Compile flags " ${flags})
endif(use_flags)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/build)

SET(CMAKE_CONFIGURATION_TYPES "Debug;Release")

# add the binary tree to the search path for include files
# so that we will find TutorialConfig.h
include_directories("${PROJECT_SOURCE_DIR}")

file(GLOB Sources "*.cpp")

add_executable("${CMAKE_PROJECT_NAME}.1" ${Sources})