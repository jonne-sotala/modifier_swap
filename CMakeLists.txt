cmake_minimum_required(VERSION 3.0)

project(modifier_swap)

add_executable(modifier_swap modifier_swap.c)
target_compile_options(modifier_swap PRIVATE -Wall -Wextra)

install(TARGETS modifier_swap RUNTIME DESTINATION bin)
