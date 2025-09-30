cmake_minimum_required(VERSION 3.20)

project(rtems-template ASM C CXX)

# Start RTEMS integration
include(tools/cmake/rtems.cmake)
rtems_cmd_init()

# Add the executable
rtems_add_executable(
    rtems-template

    src/main.c
)

target_link_libraries(
    rtems-template PRIVATE

    ntp
    bsd
    rtemscpu
    rtemsbsp
    stdc++
    c
    m
)
