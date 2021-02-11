cmake_minimum_required(VERSION 2.8.3)
project(ur3e_dual_control)

find_package(catkin REQUIRED COMPONENTS
  control_msgs
  controller_manager
  effort_controllers
  gripper_action_controller
  joint_state_controller
  joint_trajectory_controller
  ur3_description
  robot_state_publisher
  sensor_msgs
  trajectory_msgs
)

catkin_package()

include_directories(${catkin_INCLUDE_DIRS})
