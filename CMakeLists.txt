cmake_minimum_required(VERSION 3.25...4.3.2)

project(Template VERSION 0.0.1)

include(CTest)
include(cmake/Checks.cmake)
include(cmake/CompileOptions.cmake)

CHECK_GIT_SUBMODULES()

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

add_executable(${PROJECT_NAME})
add_subdirectory(src)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

target_link_libraries(${PROJECT_NAME} PRIVATE compile_options)

option(${PROJECT_NAME}_ENABLE_TESTING "Enable building of tests" OFF)
option(${PROJECT_NAME}_ENABLE_BENCHMARK "Enable building of benchmarks" OFF)
option(${PROJECT_NAME}_ENABLE_EXAMPLES "Enable building of examples" OFF)

if(${PROJECT_NAME}_ENABLE_TESTING)
    message(STATUS "Building Unit Tests")
    enable_testing()
    add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/test)
endif()

if(${PROJECT_NAME}_ENABLE_BENCHMARK)
    message(STATUS "Building Benchmarks")
    add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/bench)
endif()

if(${PROJECT_NAME}_ENABLE_EXAMPLES)
    message(STATUS "Building Examples")
    add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/examples)
endif()
