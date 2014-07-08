cmake_minimum_required(VERSION 2.8.3)

project(dynamic_graph_actionlib)

find_package(catkin REQUIRED COMPONENTS
  actionlib
  actionlib_msgs
  message_generation
  roscpp
  rospy
  std_msgs
)

add_action_files(
  DIRECTORY action
  FILES ExecuteMotionPlan.action  RunDynamicGraphCommands.action)

generate_messages(
  DEPENDENCIES actionlib_msgs std_msgs  # Or other packages containing msgs
)

catkin_package(
  CATKIN_DEPENDS actionlib_msgs message_runtime std_msgs
)

# Python installation rules.
include(cmake/base.cmake)
include(cmake/python.cmake)
FINDPYTHON()

add_subdirectory(src)
