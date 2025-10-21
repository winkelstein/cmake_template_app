cmake_minimum_required(VERSION 3.10)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

file(GLOB PROJECT_SOURCES ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp)
set(PROJECT_INCLUDE "${CMAKE_SOURCE_DIR}/include")

set(SOURCES 
            ${PROJECT_SOURCES})

set(INCLUDES
            ${PROJECT_INCLUDE})

set(LIBRARIES
              foo)

add_subdirectory(foo)

add_executable(${CMAKE_PROJECT_NAME} ${SOURCES})
target_include_directories(${CMAKE_PROJECT_NAME} PRIVATE ${INCLUDES})
target_link_libraries(${CMAKE_PROJECT_NAME} ${LIBRARIES})