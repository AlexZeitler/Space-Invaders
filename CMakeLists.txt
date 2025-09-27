cmake_minimum_required(VERSION 3.16)
project(SpaceInvaders LANGUAGES CXX)

# C++17 global festlegen
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# Standard-Build-Type (falls nicht angegeben)
if(NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE RelWithDebInfo CACHE STRING "Build type" FORCE)
endif()

# Compiler-Warnings
if(CMAKE_CXX_COMPILER_ID MATCHES "GNU|Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# Unterordner mit Code
add_subdirectory(src)

# Dokumentation optional
option(BUILD_DOCS "Build documentation" ON)
if(BUILD_DOCS)
  find_package(Doxygen)
  if(DOXYGEN_FOUND)
    add_subdirectory(docs)
  else()
    message(STATUS "Doxygen nicht gefunden – Doku wird übersprungen.")
  endif()
endif()
