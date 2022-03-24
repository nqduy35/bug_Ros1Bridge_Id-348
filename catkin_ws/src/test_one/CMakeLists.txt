cmake_minimum_required(VERSION 2.8.3)
project(test_one)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  std_msgs
	message_generation
)

# Generate messages in the 'msg' folder
add_message_files(
	DIRECTORY msg
  FILES
  	Data.msg
  	Info.msg
)

# Generate services in the 'srv' folder
add_service_files(
	DIRECTORY srv
  FILES
  	Print.srv
)

# Generate added messages and services with any dependencies listed here
generate_messages(
  DEPENDENCIES
  	std_msgs
)

catkin_package(
	CATKIN_DEPENDS
  	std_msgs
		message_runtime
)

###########
## Build ##
###########

include_directories(
 	include
  	${catkin_INCLUDE_DIRS}
)
