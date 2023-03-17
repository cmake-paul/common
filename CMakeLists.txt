add_library(common INTERFACE)

add_subdirectory(include)

add_library(common_umbrella INTERFACE)

target_link_libraries(
    common_umbrella
    INTERFACE
    common
)
