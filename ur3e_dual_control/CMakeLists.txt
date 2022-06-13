cmake_minimum_required(VERSION 2.8.3)
project(ur3e_dual_control)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  std_msgs
  message_generation
)

## Generate services in the 'srv' folder
add_service_files(
  DIRECTORY
    srv
  FILES
    ExecuteMoveItPlan.srv
)

## Generate added messages and services with any dependencies listed here
generate_messages(
  DEPENDENCIES
  std_msgs
)

###################################
## catkin specific configuration ##
###################################
catkin_package(
  CATKIN_DEPENDS message_runtime std_msgs
)

###########
## Build ##
###########

include_directories(
  include ${catkin_INCLUDE_DIRS}
)

catkin_install_python(PROGRAMS scripts/handle_moveit_service.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)