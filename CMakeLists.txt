
# This file was gererated by the build system used internally in the Yandex monorepo.
# Only simple modifications are allowed (adding source-files to targets, adding simple properties
# like target_include_directories). These modifications will be ported to original
# ya.make files by maintainers. Any complex modifications which can't be ported back to the
# original buildsystem will not be accepted.


cmake_minimum_required(VERSION 3.15)
project(YDB LANGUAGES)

set(BUILD_SHARED_LIBS Off)
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_EXTENSIONS Off)
set(YDB_MAX_LINK_JOBS 5 CACHE STRING "Maximum parallel link jobs for Ninja generator")
set_property(GLOBAL PROPERTY JOB_POOLS link_jobs=${YDB_MAX_LINK_JOBS})
set(CMAKE_JOB_POOL_LINK link_jobs)

list(APPEND CMAKE_MODULE_PATH ${CMAKE_BINARY_DIR} ${CMAKE_SOURCE_DIR}/cmake)
include_directories(${CMAKE_SOURCE_DIR} ${CMAKE_BINARY_DIR})
list(APPEND CMAKE_CTEST_ARGUMENTS "--output-on-failure")
enable_testing()
include(cmake/global_flags.cmake)
if (CMAKE_SYSTEM_PROCESSOR STREQUAL "x86_64" AND UNIX AND NOT APPLE AND NOT ANDROID)
  include(CMakeLists.linux.txt)
elseif (APPLE)
  include(CMakeLists.darwin.txt)
endif()
