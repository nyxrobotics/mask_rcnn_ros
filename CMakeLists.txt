cmake_minimum_required(VERSION 3.0.2)
project(mask_rcnn_ros)

## Compile as C++11, supported in ROS Kinetic and newer
add_compile_options(-std=c++11)

find_package(
  catkin REQUIRED
  COMPONENTS roscpp
             rospy
             std_msgs
             sensor_msgs
             cv_bridge
             image_transport
             message_generation
)

find_package(OpenCV REQUIRED)
find_package(Python3 REQUIRED COMPONENTS Interpreter Development)

catkin_package(
  CATKIN_DEPENDS
    roscpp
    rospy
    std_msgs
    sensor_msgs
    cv_bridge
    image_transport
)

include_directories(${catkin_INCLUDE_DIRS} ${OpenCV_INCLUDE_DIRS})

catkin_install_python(
  PROGRAMS scripts/mask_rcnn_node.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
