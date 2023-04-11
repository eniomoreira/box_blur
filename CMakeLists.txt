cmake_minimum_required(VERSION 3.0)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Argument with stb include dir
set(STB_INCLUDE_DIR  "/usr/include/stb")

# Check if the stb_image.h and stb_image_write.h headers exist
if(EXISTS "${STB_INCLUDE_DIR}/stb_image.h" AND EXISTS "${STB_INCLUDE_DIR}/stb_image_write.h")
    message(STATUS "Found stb headers in ${STB_INCLUDE_DIR}")
else()
    message(FATAL_ERROR "Could not find stb headers in ${STB_INCLUDE_DIR}")
endif()

# Add the stb include directory
include_directories(${STB_INCLUDE_DIR})

project(box_blur)

set(SOURCE box_blur.cpp)

add_executable(${PROJECT_NAME} ${SOURCE})

set_target_properties(${PROJECT_NAME} PROPERTIES LINK_LIBRARIES -pthread)