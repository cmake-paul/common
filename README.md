# `common`

Repository acting as CMake `INTERFACE` library to model the interface common to all platforms.

If the above does not ring any bells, check out [CMake PAUL's organization page](https://github.com/cmake-paul) first.

## Usage

Include this repository via

```cmake
include(FetchContent)

FetchContent_Declare(
    Common
    GIT_REPOSITORY https://github.com/cmake-paul/common.git
    GIT_TAG main
)

FetchContent_MakeAvailable(Common)
```

Then link against the target `CommonUmbrella`.
