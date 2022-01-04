cmake_minimum_required(VERSION 3.15)
project(findopenmp-crash VERSION 0.1.0 LANGUAGES C CXX)
message(STATUS "Configuring ${PROJECT_NAME} version ${PROJECT_VERSION} using CMake ${CMAKE_VERSION}")

add_library(findopenmp-crash SHARED findopenmp-crash.cpp)

set_target_properties(findopenmp-crash PROPERTIES
    VERSION "${PROJECT_VERSION}"
    SOVERSION 8
    FRAMEWORK TRUE
    FRAMEWORK_VERSION A
    MACOSX_FRAMEWORK_IDENTIFIER com.github.ferdnyc.openmp.reproducer
    MACOSX_FRAMEWORK_SHORT_VERSION_STRING "${PROJECT_VERSION}"
    MACOSX_FRAMEWORK_BUNDLE_VERSION "${PROJECT_VERSION}"
)

find_package(OpenMP REQUIRED)

target_link_libraries(findopenmp-crash PUBLIC
    OpenMP::OpenMP_CXX)
