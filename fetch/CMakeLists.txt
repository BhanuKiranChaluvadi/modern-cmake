cmake_minimum_required(VERSION 3.14)

project(FetchExample LANGUAGES CXX)

include(FetchContent)
include(CTest)

FetchContent_Declare(
  Catch2
  GIT_REPOSITORY https://github.com/catchorg/Catch2.git
  GIT_TAG        v2.13.0
)
FetchContent_MakeAvailable(Catch2)

message(STATUS "Catch include dir: ${catch2_SOURCE_DIR}/include")

add_executable(fetch_example main.cpp)
target_link_libraries(fetch_example PRIVATE Catch2::Catch2)
add_test(NAME fetch_example COMMAND fetch_example)