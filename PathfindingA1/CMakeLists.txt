cmake_minimum_required(VERSION 3.7)   # VS_STARTUP_PROPERTY

if (WIN32)  # MSVS is unset before "project"
  set(CMAKE_TOOLCHAIN_FILE "C://vcpkg-export-20181216-145512//scripts//buildsystems//vcpkg.cmake") # n.b. 64-bit
#  set(CMAKE_TOOLCHAIN_FILE ${CMAKE_TOOLCHAIN_FILE} "$ENV{VCPKG_ROOT}//scripts//buildsystems//vcpkg.cmake")
endif ()

set(name astar-cities)
project(${name})

add_executable(${name} ${name}.cpp)

set(Boost_USE_STATIC_LIBS ON)     # only find static libs
find_package(Boost REQUIRED) # COMPONENTS filesystem system)

if (WIN32)
  target_include_directories(${name} PRIVATE ${Boost_INCLUDE_DIRS})
  set_property(DIRECTORY PROPERTY VS_STARTUP_PROJECT ${name})
endif (WIN32)



