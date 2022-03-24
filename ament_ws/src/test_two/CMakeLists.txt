cmake_minimum_required(VERSION 3.5)
project(test_two)

# Default to C99
if(NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 99)
endif()

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
find_package(ament_cmake_python REQUIRED)
find_package(rclcpp REQUIRED)
find_package(rclpy REQUIRED)
find_package(std_msgs REQUIRED)
find_package(builtin_interfaces REQUIRED)
find_package(rosidl_default_generators REQUIRED)

set(msg_files
	"msg/Data.msg"
	"msg/Info.msg"
)

set(srv_files
	"srv/Print.srv"
)

rosidl_generate_interfaces(${PROJECT_NAME}
	${msg_files}
	${srv_files}
	
	DEPENDENCIES
		std_msgs
)

ament_package()
