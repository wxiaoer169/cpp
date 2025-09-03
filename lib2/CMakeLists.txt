add_library(math2)
target_sources(math2
  PUBLIC FILE_SET CXX_MODULES FILES math2.cppm 
  PUBLIC math2.cpp
)
target_compile_features(math2 PUBLIC cxx_std_23)
set_target_properties(math2 PROPERTIES CXX_EXTENSIONS OFF)
