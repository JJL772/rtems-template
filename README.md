# rtems-template

Template for RTEMS applications that want to use CMake as their build system.

Also intended to be used with the SLAC rtems-top. See: https://github.com/JJL772/rtems-top

## Building

To configure for all supported architectures:
```
make -f Makefile.conf
```

Building for i.e. rtems7-pc686-qemu:
```
make -C build-cmake/build-rtems7-pc686-qemu
```

## Running

```
./tools/run-i386-qemu.sh ./build-cmake/build-rtems7-pc686-qemu
```

