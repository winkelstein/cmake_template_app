cmake_minimum_required(VERSION 3.10)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

file(GLOB PROJECT_SOURCES ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp)
set(PROJECT_INCLUDE "${CMAKE_SOURCE_DIR}/include")

set(SOURCES 
            ${PROJECT_SOURCES})

set(INCLUDES
            ${PROJECT_INCLUDE})


add_library(foo ${SOURCES})
target_include_directories(foo PRIVATE ${INCLUDES})