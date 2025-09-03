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

add_library(math)
target_sources(math
  PUBLIC FILE_SET CXX_MODULES FILES lib/math.cppm 
  PUBLIC lib/math.cpp
)
target_compile_features(math PUBLIC cxx_std_23)
set_target_properties(math PROPERTIES CXX_EXTENSIONS OFF)

add_library(math2)
target_sources(math2
  PUBLIC FILE_SET CXX_MODULES FILES lib2/math2.cppm 
  PUBLIC lib2/math2.cpp
)
target_compile_features(math2 PUBLIC cxx_std_23)
set_target_properties(math2 PROPERTIES CXX_EXTENSIONS OFF)

add_executable(yoyo src/main.cpp )
target_link_libraries(yoyo PRIVATE math math2)

add_executable(lulu src2/main2.cpp )
target_link_libraries(lulu PRIVATE math math2)
