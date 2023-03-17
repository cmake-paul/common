add_library(common INTERFACE)

add_subdirectory(include)

add_library(common_umbrella INTERFACE)

target_link_libraries(
    common_umbrella
    INTERFACE
    common
)

function(register_with_common)
    set(prefix RI_ARG)
    set(noValues)
    set(singleValues IMPLEMENTATION)
    set(multiValues)

    cmake_parse_arguments(
        ${prefix}
        "${noValues}" "${singleValues}" "${multiValues}"
        ${ARGN}
    )

    if(NOT RI_ARG_IMPLEMENTATION)
        message(FATAL_ERROR "Missing keyword IMPLEMENTATION.")
    endif()

    if(NOT TARGET ${RI_ARG_IMPLEMENTATION})
        message(FATAL_ERROR "Target '${RI_ARG_IMPLEMENTATION}' specified as implementation does not exist.")
    endif()

    target_link_libraries(
        common_umbrella
        INTERFACE
        ${RI_ARG_IMPLEMENTATION}
    )
endfunction()
