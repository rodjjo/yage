find_package(Threads REQUIRED)

file(GLOB SRCS "${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp")

add_executable(testwrappers ${SRCS})

TARGET_LINK_LIBRARIES(testwrappers
    gtest
    gmock
)

add_test(NAME testwrappers 
        COMMAND testwrappers)
