cmake_minimum_required(VERSION 3.0 FATAL_ERROR)
project(custom_ops)

find_package(Torch REQUIRED)

add_executable(example_loading example_loading.cpp)
target_link_libraries(example_loading "${TORCH_LIBRARIES}")
set_property(TARGET example_loading PROPERTY CXX_STANDARD 17)