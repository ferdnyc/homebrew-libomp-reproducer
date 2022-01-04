cmake_minimum_required(VERSION 3.0.0)
project(findopenmp-crash VERSION 0.1.0 LANGUAGES CXX)
message(STATUS "Configuring ${PROJECT_NAME} version ${PROJECT_VERSION} using CMake ${CMAKE_VERSION}")

add_library(findopenmp-crash SHARED findopenmp-crash.cpp)

find_package(OpenMP REQUIRED)

target_link_libraries(findopenmp-crash PRIVATE
    OpenMP::OpenMP_CXX)
