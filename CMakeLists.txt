project(yage C CXX)

include(ExternalProject)

cmake_minimum_required(VERSION 3.18.2 FATAL_ERROR)

set(CMAKE_CXX_STANDARD 14)

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/build/lib")
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/build/lib")
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/build/bin")


ExternalProject_Add (gtest
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
