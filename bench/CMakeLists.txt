set(BENCHMARKS
)

set(BENCHMARK_ENABLE_TESTING OFF CACHE BOOL "" FORCE)
set(BENCHMARK_ENABLE_GTEST_TESTS OFF CACHE BOOL "" FORCE)
set(BENCHMARK_ENABLE_LIBPFM OFF CACHE BOOL "" FORCE)
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../lib/googlebenchmark ${CMAKE_CURRENT_BINARY_DIR}/../lib/googlebenchmark)

get_target_property(BENCH_INCLUDES benchmark INTERFACE_INCLUDE_DIRECTORIES)
set_target_properties(benchmark PROPERTIES
    INTERFACE_SYSTEM_INCLUDE_DIRECTORIES "${BENCH_INCLUDES}"
)

foreach(BENCH ${BENCHMARKS})
    add_executable(${BENCH} ${BENCH}.cpp)

    target_link_libraries(${BENCH} PRIVATE
        ${PROJECT_NAME}
        benchmark_main
        compile_options
        sanitizers
    )

endforeach()
