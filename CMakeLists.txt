cmake_minimum_required(VERSION 3.10)
project(MS_RPC_SERVER)

include(${CMAKE_BINARY_DIR}/Debug/generators/conan_toolchain.cmake)

include_directories(/usr/include)
include_directories(.)
include_directories(epmapper)
include_directories(netlogon)
include_directories(utils)

link_directories(/usr/lib)

add_compile_options("-g")

add_subdirectory(epmapper)
add_subdirectory(netlogon)
add_subdirectory(utils)

add_executable(msrpcserver
  main.cpp
)

target_link_libraries(msrpcserver
epmserver
utils
netlogon
${CONAN_LIBS}
)
