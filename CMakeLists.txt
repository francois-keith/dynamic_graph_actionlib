cmake_minimum_required(VERSION 2.4.6)

project(dynamic_graph_actionlib)
include(cmake/base.cmake)

find_package(catkin
  REQUIRED COMPONENTS actionlib_msgs roscpp rospy std_msgs message_generation)

add_action_files(
  DIRECTORY action
  FILES ExecuteMotionPlan.action  RunDynamicGraphCommands.action)

generate_messages(
  DEPENDENCIES actionlib_msgs std_msgs  # Or other packages containing msgs
)

catkin_package(
  CATKIN_DEPENDS actionlib_msgs message_runtime std_msgs
)


#include_directories(include)

# Python installation rules.
include(cmake/python.cmake)
FINDPYTHON()

add_subdirectory(src)
