cmake_minimum_required(VERSION 3.4)
project(lab05)

set(CMAKE_CXX_STANDARD 14)

add_subdirectory("${CMAKE_CURRENT_SOURCE_DIR}/third-party/gtest" "gtest")

add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/banking)

add_executable(test ${CMAKE_CURRENT_SOURCE_DIR}/tests/test.cpp)

if (COVERAGE)
    target_compile_options(test PRIVATE --coverage)
    target_link_libraries(test PRIVATE --coverage)
endif()

target_include_directories(test PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/banking)

target_link_libraries(test PRIVATE gtest gtest_main gmock_main banking)
