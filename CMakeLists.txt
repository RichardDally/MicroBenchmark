cmake_minimum_required(VERSION 2.8)
project(MicroBenchmark CXX)

set(CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/cmake_modules" ${CMAKE_MODULE_PATH})
find_package(GoogleBenchmark REQUIRED)

include_directories(${benchmark_INCLUDE_DIRS})
include_directories(headers)

file(GLOB_RECURSE SOURCE_FILES headers/* src/*)

add_executable(MicroBenchmark ${SOURCE_FILES})

target_link_libraries(MicroBenchmark ${benchmark_LIBRARIES})
if ("${CMAKE_SYSTEM_NAME}" MATCHES "Windows")                                                                                                                                                    
    target_link_libraries(MicroBenchmark Shlwapi)
endif()

