cmake_minimum_required(VERSION 4.4.0)

project(moreCMake)

set(SOURCES
    "src/main.cpp"
    "src/a.cpp"
)

add_executable(${PROJECT_NAME} ${SOURCES})


target_include_directories(${PROJECT_NAME} PRIVATE
	${PROJECT_SOURCE_DIR}/include
)

include(FetchContent)
FetchContent_Declare(
  googletest
  URL https://github.com/google/googletest/archive/03597a01ee50ed33e9dfd640b249b4be3799d395.zip
)

enable_testing()
add_subdirectory(tests)


add_executable(
  hello_test
  "tests/hello_tests.cpp"
)
target_link_libraries(
  hello_test
  GTest::gtest_main
)

include(GoogleTest)
gtest_discover_tests(hello_test)