cmake_minimum_required(VERSION 3.10)
project(JenkinsDemo)

set(CMAKE_CXX_STANDARD 11)

# 1. Enable testing capabilities
enable_testing()

add_executable(my_app main.cpp)

# 2. Add a test that checks if the app runs and exits with status 0
add_test(NAME RunTest COMMAND my_app)