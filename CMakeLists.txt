cmake_minimum_required(VERSION 2.8.3)

project(model_pose_store)

## Add support for C++11, supported in ROS Kinetic and newer
add_definitions(-std=c++11)

# Load catkin and all dependencies required for this package
find_package(catkin REQUIRED COMPONENTS
  roscpp
  gazebo_ros
  rospy
  rviz
  std_msgs
)

catkin_python_setup()
# Depend on system install of Gazebo
find_package(gazebo REQUIRED)

link_directories(${GAZEBO_LIBRARY_DIRS})
include_directories(${Boost_INCLUDE_DIR} ${catkin_INCLUDE_DIRS} ${GAZEBO_INCLUDE_DIRS})

catkin_package(
  DEPENDS
	roscpp
	gazebo_ros
	rospy
	rviz
	std_msgs
)
catkin_install_python(PROGRAMS bin/store_models
	DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})
