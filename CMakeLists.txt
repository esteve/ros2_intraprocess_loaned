cmake_minimum_required(VERSION 3.5)

project(intraprocess_loaned)

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED)

add_executable(intraprocess_loaned
  src/intraprocess_loaned/intraprocess_loaned.cpp)
target_link_libraries(intraprocess_loaned
  rclcpp::rclcpp
  ${std_msgs_TARGETS})

install(TARGETS
  intraprocess_loaned
  DESTINATION lib/${PROJECT_NAME})


if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
