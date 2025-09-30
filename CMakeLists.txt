cmake_minimum_required(VERSION 3.20)

project(rtems-template ASM C CXX)

# Start RTEMS integration
include(tools/cmake/rtems.cmake)
rtems_cmake_init()

# Add the executable
rtems_add_executable(
    rtems-template

    src/main.c
)

target_link_libraries(
    rtems-template PRIVATE ntp
)

if ("${RTEMS_NETWORKING_STACK}" STREQUAL "BSD")
    target_link_libraries(
        rtems-template PRIVATE bsd
    )
elseif ("${RTEMS_NETWORKING_STACK}" STREQUAL "LEGACY")
    target_link_libraries(
        rtems-template PRIVATE networking
    )
endif()

if ("${RTEMS_ARCH}" STREQUAL "i386" OR "${RTEMS_ARCH}" STREQUAL "powerpc")
    target_link_libraries(
        rtems-template PRIVATE debugger
    )
endif()

target_link_libraries(
    rtems-template PRIVATE

    ntp
    rtemscpu
    rtemsbsp
    stdc++
    c
    m
)
