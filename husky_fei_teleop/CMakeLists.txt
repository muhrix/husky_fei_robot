cmake_minimum_required(VERSION 2.8.3)
project(husky_fei_teleop)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED roscpp rospy std_msgs geometry_msgs sensor_msgs)

catkin_package(
  CATKIN_DEPENDS roscpp rospy std_msgs geometry_msgs sensor_msgs
)

include_directories(${catkin_INCLUDE_DIRS})

add_executable(keyboard_teleop src/keyboard_teleop.cpp)

target_link_libraries(keyboard_teleop
  ${catkin_LIBRARIES}
)

install(TARGETS keyboard_teleop
   ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
   LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
   RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

install(
  DIRECTORY launch 
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)

install(
  PROGRAMS scripts/joystick_teleop
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
