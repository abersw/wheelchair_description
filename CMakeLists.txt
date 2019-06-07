cmake_minimum_required(VERSION 2.8.3)
project(wheelchair_description)

find_package(catkin REQUIRED)
catkin_package()

find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  rviz
  std_msgs
  urdf
)

if(CATKIN_ENABLE_TESTING)
   find_package(roslaunch REQUIRED)
   roslaunch_add_file_check(launch)
endif()

catkin_package(
#  LIBRARIES tango_description
  CATKIN_DEPENDS roscpp rospy rviz std_msgs urdf xacro
#  DEPENDS system_lib
)

install(DIRECTORY launch rviz urdf 
DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})

add_executable(parser src/parser.cpp)
target_link_libraries(parser ${catkin_LIBRARIES})