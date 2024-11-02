cmake_minimum_required(VERSION 3.4...3.18)
set(PROJ_NAME geek_py)

project(${PROJ_NAME})

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(THIRD_PARTY_DIR ${PROJECT_SOURCE_DIR}/third-party)
set(PYBIND11_HEADER_PATH ${THIRD_PARTY_DIR}/pybind11/include)
set(PYBIND11_HEADER_PATH ${THIRD_PARTY_DIR}/geek/include)

include_directories(${PYBIND11_HEADER_PATH})

add_subdirectory(${THIRD_PARTY_DIR}/geek)
add_subdirectory(${THIRD_PARTY_DIR}/pybind11)

pybind11_add_module(${PROJ_NAME} src/main.cpp)

# EXAMPLE_VERSION_INFO is defined by setup.py and passed into the C++ code as a
# define (VERSION_INFO) here.
target_compile_definitions(${PROJ_NAME}
                           PRIVATE VERSION_INFO=${EXAMPLE_VERSION_INFO})