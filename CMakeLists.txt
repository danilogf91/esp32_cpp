cmake_minimum_required(VERSION 3.8...3.16) # CPP 17 support starts at v3.8, GSL up to v3.16
set(CMAKE_CXX_STANDARD 17)

#set(EXTRA_COMPONENT_DIRS $ENV{IDF_PATH}/examples/common_components/protocol_examples_common application core)
list(APPEND EXTRA_COMPONENT_DIRS application core)

include($ENV{IDF_PATH}/tools/cmake/project.cmake)

project(greenGiant)
idf_build_set_property(COMPILE_OPTIONS "-Wno-dev" APPEND)

# Setup include directory
add_subdirectory(libraries/GSL)
#include_directories(${CMAKE_PROJECT_NAME} PUBLIC ${PROJECT_SOURCE_DIR} libraries/GSL)
target_link_libraries(${COMPONENT_LIB} GSL)