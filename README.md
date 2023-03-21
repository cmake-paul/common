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

When implementing something that depends on the interface defined in `common`, link against the target `CommonUmbrella`.

When providing an implementation of said interface, register the implementation using `register_with_common(IMPLEMENTATION ${implementing_target})`.
