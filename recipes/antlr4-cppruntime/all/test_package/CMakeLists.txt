cmake_minimum_required(VERSION 3.15)
project(test_package LANGUAGES CXX)

find_package(antlr4-runtime REQUIRED CONFIG)

add_executable(${PROJECT_NAME} test_package.cpp)
if(TARGET antlr4_shared)
    target_link_libraries(${PROJECT_NAME} PRIVATE antlr4_shared)
else()
    target_link_libraries(${PROJECT_NAME} PRIVATE antlr4_static)
endif()
target_compile_features(${PROJECT_NAME} PRIVATE cxx_std_17)
