cmake_minimum_required(VERSION 3.14...3.18)

project(FetchContentExample LANGUAGES CXX)

include(FetchContent)
include(CTest)

# fetch doctest
FetchContent_Declare(
  doctest
  GIT_REPOSITORY https://github.com/onqtam/doctest.git
  GIT_TAG 2.4.0
)

set(DOCTEST_WITH_TESTS OFF)
# include doctest into build
FetchContent_MakeAvailable(doctest)

add_executable(fetchcontent_example main.cpp)
target_link_libraries(fetchcontent_example PRIVATE doctest::doctest)
add_test(NAME fetchcontent_example COMMAND fetchcontent_example)


