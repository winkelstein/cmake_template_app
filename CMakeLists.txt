cmake_minimum_required(VERSION 3.15)

project(cmake_template_app VERSION 1.0.0)

option(BUILD_DOCS "Build documentation with the project" ON)
option(BUILD_TESTING "Build with tests" ON)

if (BUILD_DOCS)
  include(cmake/Doxygen.cmake)
  myproject_enable_doxygen("doxygen-awesome-darkmode-toggle")
endif()

if(BUILD_TESTING)
  enable_testing()
  add_subdirectory(${CMAKE_SOURCE_DIR}/libs/googletest)
  add_subdirectory(test)
endif()

add_subdirectory(${CMAKE_SOURCE_DIR}/src bin)

# Here's dependencies