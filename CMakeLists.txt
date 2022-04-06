cmake_minimum_required(VERSION 3.16)
project(cmake-bug CXX)

add_executable(test test.cpp)

include(CheckCXXCompilerFlag)
set(_flags -W3 -Wextra -Werror)
foreach(_flag ${_flags})
  unset(_flag_supported)
  check_cxx_compiler_flag(${_flag} _flag_supported)
  if(${_flag_supported})
    target_compile_options(test PRIVATE ${_flag})
  endif()
endforeach()
