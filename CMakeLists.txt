cmake_minimum_required(VERSION 3.18.2 FATAL_ERROR)

project(yage C CXX)

include(ExternalProject)

set(CMAKE_CXX_STANDARD 14)

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/build/lib")
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/build/lib")
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/build/bin")

enable_testing()

ExternalProject_Add (googletests
	URL https://github.com/google/googletest/archive/release-1.10.0.tar.gz
	SOURCE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/third-party/google-test"
    PREFIX "${CMAKE_CURRENT_SOURCE_DIR}/build/gtest"
    # INSTALL_DIR "${CMAKE_CURRENT_SOURCE_DIR}/build/"
    # CMAKE_ARGS ""
    # DOWNLOAD_COMMAND "" # Disable download step
    # CONFIGURE_COMMAND "" # Disable all other steps
    # BUILD_COMMAND ""
    INSTALL_COMMAND ""
)

ExternalProject_Get_Property(googletests source_dir binary_dir)

include_directories(
    "${CMAKE_CURRENT_SOURCE_DIR}/libraries/lua"
    "${CMAKE_CURRENT_SOURCE_DIR}/third-party/google-test/googlemock/include"
    "${CMAKE_CURRENT_SOURCE_DIR}/third-party/google-test/googletest/include"
    "${CMAKE_CURRENT_SOURCE_DIR}/yage-common/wrappers"
)

link_directories("${CMAKE_CURRENT_SOURCE_DIR}/build/gtest/src/googletests-build/lib")

add_subdirectory("yage-common/wrappers/tests")

