cmake_minimum_required(VERSION 3.15)

project(cmake_template_app VERSION 1.0.0)

option(BUILD_DOCS "Build documentation with the project" ON)
option(BUILD_TESTING "Build with tests" ON)

if(MSVC)
  add_compile_options(/W4)
else()
  add_compile_options(-Wall -Werror -Wextra -Wpedantic)
endif()

if(BUILD_DOCS)
  include(cmake/Doxygen.cmake)
  project_enable_doxygen("doxygen-awesome-darkmode-toggle" include)
endif()

if(BUILD_TESTING)
  enable_testing()
  add_subdirectory(libs/googletest)
  add_subdirectory(test)
endif()

add_subdirectory(src bin)
target_include_directories(${PROJECT_NAME} PRIVATE include)

# Here's dependencies