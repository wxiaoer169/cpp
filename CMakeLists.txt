cmake_minimum_required(VERSION 3.26.0)
project(CXXModules CXX)

# turn on the experimental API
if(CMAKE_VERSION VERSION_GREATER_EQUAL 3.28.0)
  # Assume that C++ sources do import modules
    cmake_policy(SET CMP0155 NEW)
else()
  message(FATAL_ERROR "Version lower than 3.26 not supported")
endif()

# Libc++ has no support compiler extensions for modules.
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_STANDARD 23)

add_subdirectory(lib)

add_subdirectory(lib2)

add_subdirectory(src)

add_subdirectory(src2)

