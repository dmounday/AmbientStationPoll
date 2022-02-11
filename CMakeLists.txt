cmake_minimum_required(VERSION 3.18)
# 
# Set Tool chain variables
# set(CMAKE_TOOLCHAIN_FILE RPiCrossTools.cmake)

project(AmbientPoll VERSION 1.0
        DESCRIPTION "Poll live data from Ambient Weather Station"
  LANGUAGES CXX)
  
include(CMakePrintHelpers)
include(ExternalProject)
cmake_print_variables(CMAKE_PROJECT_NAME PROJECT_NAME CMAKE_INSTALL_PREFIX
                      CMAKE_SYSTEM_PREFIX_PATH
                      CMAKE_BINARY_DIR)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON) 
set(CMAKE_CXX_EXTENSIONS OFF)
set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads)

add_executable( AmbientPoll src/AmbientStation.cpp)

# find_package(Threads) doesn't work right on Ubuntu linux so just force the 
# pthreads library
target_link_libraries( AmbientPoll PRIVATE -pthread)








