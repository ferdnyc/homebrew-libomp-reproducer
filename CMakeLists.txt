cmake_minimum_required(VERSION 3.15)
project(testOpenMP VERSION 0.1.0 LANGUAGES C CXX)
message(STATUS "Configuring ${PROJECT_NAME} version ${PROJECT_VERSION} using CMake ${CMAKE_VERSION}")

option(USE_PACKAGE "Use find_package(OpenMP)" ON)

add_library(testOpenMP SHARED testOpenMP.cpp)

set_target_properties(testOpenMP PROPERTIES
    VERSION "${PROJECT_VERSION}"
    SOVERSION 8
    FRAMEWORK TRUE
    FRAMEWORK_VERSION A
    MACOSX_FRAMEWORK_IDENTIFIER com.github.ferdnyc.openmp.reproducer
    MACOSX_FRAMEWORK_SHORT_VERSION_STRING "${PROJECT_VERSION}"
    MACOSX_FRAMEWORK_BUNDLE_VERSION "${PROJECT_VERSION}"
)

if(USE_PACKAGE)
    find_package(OpenMP REQUIRED)

    target_link_libraries(testOpenMP PUBLIC
        OpenMP::OpenMP_CXX)
else()
    target_compile_options(testOpenMP PUBLIC
        -Xclang -fopenmp)
    target_include_directories(testOpenMP PUBLIC
        /usr/local/include)
    target_link_libraries(testOpenMP PUBLIC
        /usr/local/lib/libomp.dylib)
endif()

