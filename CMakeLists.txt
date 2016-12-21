# project
cmake_minimum_required (VERSION 3.0)
project (libelas)

# directories
set (LIBELAS_SRC_DIR src)

# include directory
include_directories("${LIBELAS_SRC_DIR}")

# use sse3 instruction set
set(CMAKE_CXX_FLAGS "-msse3")

# sources
file(GLOB LIBELAS_SRC_FILES "src/*.cpp")
list(REMOVE_ITEM LIBELAS_SRC_FILES "${CMAKE_CURRENT_SOURCE_DIR}/src/main.cpp")
message(${LIBELAS_SRC_FILES})

# make release version
#set(CMAKE_BUILD_TYPE Release)

# build demo program
add_library(elas ${LIBELAS_SRC_FILES})

add_executable(elasdemo
  ${CMAKE_CURRENT_SOURCE_DIR}/src/main.cpp
  ${LIBELAS_SRC_FILES})
