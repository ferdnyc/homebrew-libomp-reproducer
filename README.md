# homebrew-libomp-reproducer

CMake's `FindOpenMP.cmake` module seems to be failing on macOS,
if the build system is generated with `-DCMAKE_OSX_ARCHITECTURES="x86_64;arm64"`.
Attempting to reproduce in a clean project here.
